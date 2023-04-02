<svelte:head>
    <title> Life Cycle </title>
    <meta name="description" content=" tick " />
</svelte:head>

<h2>
    tick 예제
</h2>

<h3>
    개념
</h3>
<pre>
    함수 tick의 목적: 화면의 갱신이 완료될때까지 기다린다.
    - 스벨트는 전체 로직의 최적화를 위해 내부 로직을 다 실행한 후에 화면을 갱신한다.
    - 로직 내에서 화면을 갱신하고 싶다면, 함수 tick을 사용하면 된다.
    - 함수 tick()은 비동기로 실행해야한다.

</pre>

<h3>
    예제를 통해 알 수 있는 것.
</h3>
<pre>
    - tick()을 실행하지 않으면, 함수 내에서 화면의 갱신이 반영되지 않는다.
    - tick()을 실행하면, 함수 내에서 화면이 갱신될 동안 기다린 후, 다음 명령어를 실행한다.
</pre>

<h3>RUN!</h3>
<p>=============================================================</p>
<script>
    import {tick} from "svelte"
    let name = "beauty";
    function withoutTick(){ //console창에 기존 화면이 출력된다.
        name = "ugly"
        const content = document.querySelector('.title');
        console.log(`without: ${content && content.innerHTML}`);
    }
    function withTick(){ //console창에 업데이트된 화면이 출력된다.
        name = "ugly"
        tick();
        const content = document.querySelector('.title');
        console.log(`with: ${content && content.innerHTML}`);
    }

</script>

<h4 class = "title" style="margin:10px">
    Hello {name};
</h4>
<button on:click={withTick}> with tick() </button>
<button on:click={withoutTick}> without tick() </button>

<p>=============================================================</p>

<h4> 실행 결과 </h4>
<img src = "src/lib/images/tick.png" width="600"/>

<h3>추가로 알면 좋은것</h3>
<pre>
    1. 동기와 비동기 공부하기
</pre>