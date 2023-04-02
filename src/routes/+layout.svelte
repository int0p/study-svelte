<script>
  import "../app.scss";
</script>

<label for="drawer-control" class="drawer-toggle"></label>

<input type="checkbox" id="drawer-control" class="drawer">
<div>
    <label for="drawer-control" class="drawer-close"></label>
    <a href="#">Home</a>
</div>

<nav>
    <a href="#">Category 1</a>
    <span>Category 2</span>
    <a href="#" class="sublink-1">Item 2.1</a>
    <span class="sublink-1">Category 2.2</span>
    <a href="#" class="sublink-2">Item 2.2.1</a>
</nav>

<slot />
