<svelte:head>
    <title> 조건, 반복, 키 </title>
    <meta name="description" content="  " />
</svelte:head>

<h2>
    조건, 반복, 키 예제
</h2>

<h3>
    개념
</h3>
<pre>
    <h4> 사용패턴 </h4>
    - 시작 블록은 #을,
    - 중간 블록은 :을,
    - 종료 블록은 /를 사용합니다.
</pre>

<h3>
    예제를 통해 알 수 있는 것.
</h3>
<pre>
    0.
</pre>


<h3>RUN!</h3>
<p>=========================</p>
<script>
    let count = 0;
    let fruits = ['Apple', 'Banana', 'Cherry']

    import Prism from 'prismjs';
    let code_script = `

    `;

    let code_html = `

    `;
    let code_css = `

    `;
    let code_svelte = `

    `;
</script>

<div style="margin:10px">
    <button on:click={() => { count += 1}}>증가!</button>
    <button on:click={() => { count -= 1}}>감소!</button>

    <h2>{count}</h2>

    <section>
        <h2>if</h2>
        {#if count > 3}
            <div>count &gt; 3</div>
        {/if}
    </section>

    <section>
        <h2>if else</h2>
        {#if count > 3}
            <div>count &gt; 3</div>
        {:else}
            <div>count &lt;= 3</div>
        {/if}
    </section>

    <section>
        <h2>if else if</h2>
        {#if count > 3}
            <div>count &gt; 3</div>
        {:else if count === 3}
            <div>count === 3</div>
        {:else}
            <div>count &lt; 3</div>
        {/if}
    </section>

    <section>
        <h2>다중 블록</h2>
        {#if count > 3}
            {#if count === 5}
                count === 5
            {:else}
                count &gt; 3
            {/if}
        {/if}
    </section>

    <h2> each </h2>
    {#each fruits as fruit}
        <div>{fruit}</div>
    {/each}


</div>
<p>=========================</p>


<h4> 코드 </h4>
<pre class="language-svelte">
    {@html Prism.highlight(code_script, Prism.languages.js)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_svelte, Prism.languages.svelte)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_html, Prism.languages.html)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_css, Prism.languages.css)}
</pre>

<h4> 콘솔 실행 결과 </h4>
<img src = "src/lib/images/" height="400"/>


<h3>추가로 알면 좋은것</h3>
<pre>
    1.
</pre>

<style>
    section {
        border: 1px solid orange;
        margin-bottom: 10px;
        padding: 10px;
    }
    h2 {
        margin: 0;
        margin-bottom: 10px;
    }
</style>