<svelte:head>
    <title> 요소 바인딩 </title>
    <meta name="description" content=" binding " />
</svelte:head>

<h2>
    예제
</h2>

<h3>
    개념
</h3>
<pre>
    <h4>this 일반 요소 바인딩</h4>
    -
    <h4>입력 요소 바인딩</h4>
    -

    <h4>편집 가능 요소 바인딩</h4>
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

</div>
<p>=========================</p>

<h4> 코드 </h4>
<pre class="language-svelte">
    {@html Prism.highlight(code_script, Prism.languages.js)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_svelte, Prism.languages.js)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_html, Prism.languages.html)}
</pre>

<pre class="language-svelte">
    {@html Prism.highlight(code_css, Prism.languages.css)}
</pre>

<h3>추가로 알면 좋은것</h3>
<pre>
    1.
</pre>