<svelte:head>
    <title> Interpolation, 보간법 </title>
    <meta name="description" content=" 내용/속성/표현식/html/debug 보간 " />
</svelte:head>

<h2>
    Interpolation, 보간법 예제
</h2>

<h3>
    개념
</h3>
<pre>
    ** 중괄호를 +로 표현함. **

    목표: 내용/속성/표현식 보간
    -. +내용/속성/표현식+
    -. 속성을 보간할땐 속성의 이름을 ""내에 적지 않아도 된다.
    -. 단방향 바인딩: script내의 변수를 html에 갖고온다.
    -. 양방향 바인딩: script내의 변수를 html에서 가져오고, html에서 변경된 값을 script변수에 update한다.
    -. 속성을 보간할 때, 속성 이름과 데이터 이름이 같으면
        - 양방향 바인딩: 데이터 이름만 적어도 된다.  (ex. bind:value=+value+ => bind:value)
        - 단방향 바인딩: 속성 이름만 적어도 된다. (ex. value=+value+ => +value+)
    -. 스벨트는 컴파일러이므로, 보간을 통해 표현식을 작성하는것을 권장한다. (event handler에서 자세히.)
        - 코드를 줄일 수 있음.

    목표: script에서 작성된 html내용을 보간할 때, html을 해석해서 화면에 보여지도록한다.
    -. +@html 변수명+
    -. 외부에서 작성한 html역시 해석하므로 보안에 주의해야한다. (xss)

    목표: 보간할 변수가 변경될때마다 콘솔에 그 값을 출력한다. (추적)
    -. +@debug 변수명+
</pre>

<h3>
    예제를 통해 알 수 있는 것.
</h3>
<pre>
    1. 양방향 데이터 바인딩
    2. html 보간
    3. 보간 대상 debug
</pre>


<h3>RUN!</h3>
<p>=========================</p>
<script>

</script>

<div style="margin:10px">

</div>
<p>=========================</p>

<h4> 실행 결과 </h4>
<img src = "src/lib/images/" height="400"/>

<h3>추가로 알면 좋은것</h3>
<pre>
    1. xss(cross site scripting) : 웹 취약점의 하나로, 웹사이트 관리자가 아닌 제 3자가 웹에 악성 스크립트를 삽입할 수 있음.
</pre>