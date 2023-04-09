
<svelte:head>
    <title> Class </title>
    <meta name="description" content=" class, global, keyframe " />
</svelte:head>

<h2>
    class 예제
</h2>

<h3>
    개념
</h3>
<pre>
    <h4> 클래스와 스타일 속성 바인딩</h4>
    - 보간법 및 클래스 지시어(class:)를 이용하여 간단하게 클래스를 추가/제거 할 수 있다.

    <h4> 스타일 유효범위(hash)와 전역화(global)</h4>
    - [style]에 선언된 css는 기본적으로 해당 컴포넌트의 유효범위를 가진다.
        - 스타일이 컴포넌트 내 요소에서만 적용된다.
        - 요소의 class에 컴포넌트에 대한 svelte-hash가 추가된다.
    - 유효범위 없이 선언하려면 <code>:global(선택자) 수정자(modifier)</code>
    - ex. <code>:global(body) margin: 6vw; </code> 으로 모든 body에 margin적용
    - 스벨트는 컴파일러이므로, 번들이 나오기 전에 전체 코드를 평가한다.
        - 사용되지 않은 css 선택자는, 스벨트가 필요치 않다고 판단하여 css 번들에 포함시키지 않는다.
        - global지시어를 사용하면, 웹 페이지에서 쓸지 안 쓸지 모르는 css요소를 번들에 포함시킬 수 있다.

    <h4>@keyframes 전역화</h4>
    - css의 animation 속성에서 사용됨.
</pre>

<h3>
    예제를 통해 알 수 있는 것.
</h3>
<pre>
    0. 스벨트 지시어 사용
        - class에 hello속성이 추가되는지는 active의 값에 의해 결정된다.
</pre>


<h3>RUN!</h3>
<p>=========================</p>
<script>

    let active = false;
    let color = {
        g: 'green',
        t: 'tomato',
    }

    import Prism from 'prismjs';
    let code_script = `
        let active = false;
        let color = {
            g: 'green',
            t: 'tomato',
        }
    `;
    let code_html = `
        <h4>class에 속성 추가/제거</h4>
        <button on:click={()=> active = !active }>Toggle active to change box color</button>
        <div class = "box" class:hello={active} >
            active: {active}
        </div>

        <h4>스타일 추가(바인딩)</h4>
        <div class = "box" style="background-color: {color.t}; color:{color.g}" >
            꼭지<br>
            토마토
        </div>
    `;

    let code_pattern = `
    [script]
      let active = true
      let valid = false
      let camelCase = true
      let color = {
        white: '#FFF',
        red: '#FF0000'
      }
      let bold = 'font-weight: bold;'

      function multiClass() {
        return 'active valid camel-case'
      }
    [/script]

    <div class={active ? 'active' : ''}>
        3항 연산자 보간
    </div>

    <div class:active={active}>
        Class 지시어(Directive) 바인딩
    </div>

    <div class:active>
        Class 지시어 바인딩 단축 형태
    </div>

    <div
            class:active
            class:valid
            class:camelCase
            class:camel-case={camelCase}>
        다중 Class 지시어 바인딩
    </div>

    <div class={multiClass()}>
        함수 실행
    </div>

    <div
            class="style-binding"
            style="
        color: {color.white};
        background-color: {color.red};
        {bold}">
        스타일 바인딩
    </div>
    `;
    let code_keyframe = `
      :global(body) {
        padding: 50px;
      }
      .box {
        width: 100px;Class & Style Binding: Pattern
        height: 100px;
        background: tomato;
        animation: zoom .4s infinite alternate;
      }
      /* -global- */
      @keyframes -global-zoom {
        0% {
          transform: scale(1);
        }
        100% {
          transform: scale(1.5);
        }
      }
    `;
</script>

<div style="margin:10px">
    <h4>class에 속성 추가/제거</h4>
    <button on:click={()=> active = !active }>Toggle active to change box color</button>
    <div class = "box" class:hello={active} >
        active: {active}
    </div>

    <h4>스타일 추가(바인딩)</h4>
    <div class = "box" style="background-color: {color.t}; color:{color.g}" >
        꼭지<br>
        토마토
    </div>
</div>
<p>=========================</p>

<h4> 코드 </h4>
<pre class="language-svelte">
    {@html Prism.highlight(code_script, Prism.languages.js)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_html, Prism.languages.js)}
</pre>

<h4> 클래스 바인딩 패턴 정리 </h4>
<pre class="language-svelte">
    {@html Prism.highlight(code_pattern, Prism.languages.html)}
</pre>

<h4> 키프레임 사용 예시 </h4>
<pre class="language-svelte">
    {@html Prism.highlight(code_keyframe, Prism.languages.css)}
</pre>

<h3>추가로 알면 좋은것</h3>
<pre>
    1. css번들, hash
    2. keyframe 애니메이션
</pre>

<style lang="scss">
    .box{
      width: 70rem;
      height: 200px;
      background-color: mediumpurple;
      text-align: center;
      color: white;
    }
    .hello{
      background-color: cornflowerblue;
    }
</style>