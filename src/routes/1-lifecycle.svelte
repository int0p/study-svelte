<svelte:head>
    <title>Life Cycle</title>
    <meta name="description" content="onMount, onDestroy, afterUpdate, beforeUpdate" />
</svelte:head>

<h2>
    onMount, onDestroy, afterUpdate, beforeUpdate 예제
</h2>

<h3>
    개념
</h3>
<pre>
    목표: 컴포넌트와 화면을 연결할꺼다.
    연결 전 - beforeUpdate
    (DOM과 data를 동기화)
    연결 됨 - onMount
    연결 후 - afterUpdate

    목표: 컴포넌트와 화면이 연결된 상태에서 data를 갱신했을 때, 화면을 바꾼다.
    화면 바꾸기 전 - beforeUpdate
    화면 바꾼 후 - afterUpdate

    목표: 컴포넌트와 화면의 연결을 해제한다.
    해제 전 - onMount
    해제 직후-  onDestroy (아직 data 남아있음)
    해제 됨

    요약:
    - onMount, onDestroy에 의해 화면에 component가 연결된(DOM생성) 직후, 연결해제되기 직전에 실행할 함수를 정의한다.
    - beforeUpdate, afterUpdate에 의해 반응성을 갖는 data가 갱신되기 전 후 실행할 함수를 정의한다.
</pre>


<h3>
    예제를 통해 알 수 있는 것.
</h3>
<pre>
    0. component의 lifecycle임에 유의해야한다. -> 동일 component에서는 mount여부를 확인 할 수 없다.
    1. toggle data로 component Ex가 화면에 보이게 할지 말지 결정한다.
    2. component가 연결됐을 때 onMount가 실행되므로 이 때 HTML요소들을 확인 할 수 있다. (counter.innerHTML가 존재하는지로 확인)
    3. data의 갱신에 의해 화면이 바뀌기 전에 beforeUpdate가, 화면이 바뀐 후 afterUpdate가 실행된다. (class counter로 확인)
    4. beforeUpdate와 afterUpdate의 대상은 갱신하고자 하는 data가 아니라, 갱신하고자 하는 화면임에 유의해야한다. (변수 count로 확인)
</pre>


<h3>RUN!</h3>
<p>================</p>
<script>
    import Ex from "./1-lifecycle-ex.svelte"

    let toggle = false;
</script>

<button on:click={()=>toggle=!toggle} > toggle counter </button>
<div style="margin:10px">
    {#if toggle}
        <Ex/>
    {/if}
</div>
<p>================</p>

<h4> 실행 결과 </h4>
<img src = "src/lib/images/lifecycle.png" height="400"/>

<h3>추가로 알면 좋은것</h3>
<pre>
    1. onMount의 return을 통해 onDestroy를 정의할 수 있다.
    2. beforeUpdate와 afterUpdate내에서 data를 갱신하면 무한루프의 위험이 있다.
</pre>