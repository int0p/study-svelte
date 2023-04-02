<script>
    import {onMount, onDestroy,afterUpdate,beforeUpdate} from "svelte";

    let count = 0;
    let counter;

    beforeUpdate(()=>{
        console.log(`>> before data Update`);
        console.log(`data가 갱신되기 전 화면 상 count = ${counter && counter.innerHTML}`); // counter가 있는 경우에 innerHTML을 출력
        console.log(`data에 저장된 값 count = ${count}`);
    })
    onMount(()=>{
        console.log("> mount됨. 등장!");
        counter = document.querySelector('.counter');
        console.log(`onMount 됐을 때 화면에 보여지는 count , ${counter.innerHTML}`);
    })
    afterUpdate(()=>{
        console.log(`> after data Update`);
        console.log(`data가 갱신된 후 화면 상 count = ${counter && counter.innerHTML}`);
    })
    onDestroy(()=>{
        console.log("> 곧 사라짐!");
        console.log(`onDestroy 됐을 때 화면에 보여졌던 count , ${counter.innerHTML}`);
    })

    function increase(){
        count += 1;
    }

</script>

<div>
    <p style="display:inline"> num =  </p>
    <div class="counter" style="display:inline">{count}</div>
    <button on:click={increase} > up </button>
</div>

