<svelte:head>
    <title> Reactivity, 반응성 </title>
    <meta name="description" content="데이터의 불변성과 가변성, 할당, label, 반응성 구문, 반응성 구문 패턴  " />
</svelte:head>

<h2>
    Reactivity, 반응성 예제
</h2>

<h3>
    개념
</h3>
<pre>
    <h4> JS문법 - 데이터의 불변성과 가변성</h4>
    - 변수에 변수를 대입하면, 메모리 주소가 전달된다.
    - 원시 데이터는 변경될 수 없다. - immutable data
        - 변수에 값을 할당하면, 변수는 값의 주소를 저장한다.
        - 변수에 값을 재할당하면, 변수는 새로운 값의 주소를 저장한다.
        - JS는 garbage collection으로, 메모리에 할당된 불필요한 데이터를 자동으로 해제한다.
    - 객체 데이터는 가변성을 갖는다. -> 데이터의 값만 변경할 수 있다.
    - 전개연산자를 사용하여 객체 데이터를 얕은복사할 수 있다.
    - 객체 데이터의 복사
        - 얕은 복사: 1 depth만 복사 (객체내 객체의 값은 복사되지 않음)
        - 깊은 복사: 가변성이 있는 모든 data를 복사. 반복문등을 통해 적용.

    <h4> 스벨트에서 반응성과 바인딩</h4>
    - 바인딩(bind:) - 부모 컴포넌트와 자식 컴포넌트 사이에 양방향 데이터 바인딩을 생성하는 방법.
        - 자식 컴포넌트의 값 변경이 부모 컴포넌트에 자동으로 반영되거나, 그 반대.
    - 반응성($:) - 데이터 변경에 따라 DOM을 효율적으로 업데이트 할 수 있는 스벨트의 핵심 기능.
        - 반응형 값이 업데이트되면 스벨트는 전체 DOM을 update할 필요 없이 컴포넌트의 관련 부분을 자동으로 렌더링한다.
        - 스벨트는 가상 DOM을 사용하지 않아 코드가 런타임에서 돌아가는게 아닌 순수한 JS로 컴파일된 코드가 동작하게된다.
            - 따라서, 수동으로 반응성을 부여해야한다.

    <h4> 할당 assignment과 반응성 </h4>
    - 스벨트는 할당을 통해 반응성 갱신이 가능하다.
    - 함수 내 한줄의 코드라도 반응성을 갖게되면, 데이터가 갱신된 후에야 화면이 갱신되므로,
        다른 코드들도 반응성을 갖게된다. (tick())

    <h4> 반응성 구문 </h4>
    - 반응성구문에서 반응성을 가지는 데이터가 갱신되면, 화면이 갱신되고, 반응성 구문이 실행된다.
    - tick()을 사용하여 반응성을 기다릴 수 있다.
    - 반응성 구문에서는 let 선언을 사용하지 않는다.

</pre>

<h3>
    예제를 통해 알 수 있는 것.
</h3>
<pre>
    0. 할당을 통해 반응성을 갖게 되는것.
        - 함수 assign내에서 변수 hobby는 hobby를 할당해줘야 값이 갱신됨.
    1. 객체의 속성에 반응성을 부여하면, 객체와 객체의 속성들 역시 반응성을 갖게된다.
        - 함수 assign내에서 user.name을 할당하면,
        스벨트의 할당표현($$isvalidate)에 user역시 명시된다.
        따라서, user와 user의 속성들 역시 반응성을 갖게된다.
    2. 함수 내에서 반응성을 갖는 변수가 있으면, 해당 변수에 매번 반응성을 부여하지 않아도 됨.
        - 함수 assign내에서 user.name이 반응성을 가지므로 user.hobby역시 반응성을 갖는다.
        - user.hobby는 할당 없이 데이터를 갱신할 수 있다.
    3. 객체데이터의 가변성.
        - 변수 hobby에 user.hobby를 할당하면, 둘은 같은 메모리주소를 가리킨다.
        - hobby의 값을 수정하면 user.hobby의 값 역시 갱신된다.
    4. 반응성 구문이 실행되는 순서
        - 함수 assign_count에 의해 변수 count값이 갱신되면,
            함수가 실행되는 중일 땐 double이 update되지 않고,
            화면이 갱신되면 반응성 구문이 실행되어 double이 update된다.
</pre>

<h3>RUN!</h3>
<p>=========================</p>
<script>
    import {tick} from 'svelte'

    let user ={
        name : "int0p",
        hobby: ["독서","기타","노래"]
    };
    let hobby = user.hobby;
    function assign(){
        user.name = "molla"; // 자동으로 객체 내 데이터에 새로운 값을 할당함.
        user.hobby.push("user.hobby에 추가된 낮잠"); // user.name에 할당할 때 user에 할당했으므로, user.hobby역시 반응성을 가짐.
        hobby.push("hobby에 추가된 취침"); // 변수 hobby는 user.hobby와 동일한 주소를 가리키므로 hobby의 갱신은 user.hobby에 반영됨.
        // hobby = hobby // 그러나 hobby자체가 반응성을 가지는것은 아니므로, 해당 코드를 작성해줘야 값이 갱신됨.
    }

    let count = 0;
    let double = 0;
    //반응성 구문
    $:{
        double = count * 2;
        console.log(`double의 값 in 반응성구문 ${double}`);
    }

    // async function assign_count_tick(){
    //     count+=1;
    //     await tick();
    //     console.log(`double의 값 in 함수 assign_count_tick ${double} -> double이 update됨. `);
    // }

    function assign_count(){
        count+=1;
        console.log(`double의 값 in 함수 assign_count = ${double} -> 아직 double 값이 update되지 않음. `);
    }
    let code = `
        let user ={
            name : "int0p",
            hobby: ["독서","기타","노래"]
        };
        let hobby = user.hobby;

        function assign(){
            user.name = "molla"; // 자동으로 객체 내 데이터에 새로운 값을 할당함.
            user.hobby.push("user.hobby에 추가된 낮잠"); // user.name에 할당할 때 user에 할당했으므로, user.hobby역시 반응성을 가짐.
            hobby.push("hobby에 추가된 취침"); // 변수 hobby는 user.hobby와 동일한 주소를 가리키므로 hobby의 갱신은 user.hobby에 반영됨.
            // hobby = hobby // 그러나 hobby자체가 반응성을 가지는것은 아니므로, 해당 코드를 작성해줘야 값이 갱신됨.
        }

        let count = 0;
        let double = 0;

        //반응성 구문
        $:{
            double = count * 2;
            console.log(\`double의 값 in 반응성구문 ${double}\`);
        }
    `;
    let code_pattern =`
        let count = 0

        // 선언
        $: double = count * 2

        // 블록
        $: {
            console.log(count)
            console.log(double)
        }

        // 함수 실행
        $: count, log()

        // 즉시 실행 함수(IIFE)
        $: count, (() => {
            console.log('iife: Heropy')
        })();

        // 조건문(If)
        $: if (count > 0) {
            console.log('if:', double)
        }

        // 반복문(For)
        $: for (let i = 0; i < 3; i += 1) {
            count
            console.log('for:', i)
        }

        // 조건문(Switch)
        $: switch (count) {
            case 1:
                console.log('switch: 1')
                break
            default:
                console.log('switch: default')
        }

        // 유효범위
        $: {
            function scope1() {
                console.log('scope1')
                function scope2() {
                    console.log('scope2')
                    function scope3() {
                        console.log('scope3', count)
                    }
                    scope3()
                }
                scope2()
            }
            scope1()
        }

        function log() {
            console.log('fn: Heropy!')
        }
        function assign() {
            count += 1
        }
    `;
</script>

<div style="margin:10px">
    <button on:click={assign}>Assign-user</button> <br>
    user-name: {user.name} <br>
    user-hobby: {user.hobby} <br>
    hobby: {hobby} <br>
    <br>

    <button on:click={assign_count}>count-up without tick()</button><br>
    count: {count} <br>
    double: {double}<br>

</div>
<p>=========================</p>

<h4> 코드 </h4>
<pre class="code" data-lang="svelte script"><code>{code}</code></pre>

<h4> 반응성 구문 패턴 </h4>
<pre class="code" data-lang="svelte script"><code>{code_pattern}</code></pre>

<h3>추가로 알면 좋은것</h3>
<pre>
    1.
</pre>