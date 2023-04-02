<script>
  import "../app.scss";
</script>

<!-- menu drawer  (spectre.css)  -->
<label for="drawer-control" class="drawer-toggle persistent"></label>

<input type="checkbox" id="drawer-control" class="drawer persistent">
<div>
    <label for="drawer-control" class="drawer-close"></label>
    <a href="#">Home</a>
    <nav>
        <a href="#">Category 1</a>
        <span>Category 2</span>
        <a href="#" class="sublink-1">Item 2.1</a>
        <span class="sublink-1">Category 2.2</span>
        <a href="#" class="sublink-2">Item 2.2.1</a>
    </nav>
</div>

<!-- menu tab-->

<!-- basic dropdown button -->
<div class="dropdown">
    <a href="." class="btn btn-link dropdown-toggle" tabindex="0">
        dropdown menu <i class="icon icon-caret"></i>
    </a>
    <!-- menu component -->
    <ul class="menu">
        ...
    </ul>
</div>


<!-- step (spectre.css) -->
<ul class="step">
    <li class="step-item">
        <a href="#" class="tooltip" data-tooltip="Step 1">Step 1</a>
    </li>
    <li class="step-item active">
        <a href="#" class="tooltip" data-tooltip="Step 2">Step 2</a>
    </li>
    <li class="step-item">
        <a href="#" class="tooltip" data-tooltip="Step 3">Step 3</a>
    </li>
    <li class="step-item">
        <a href="#" class="tooltip" data-tooltip="Step 4">Step 4</a>
    </li>
</ul>

<!-- nav-bar (mini.css)-->
<nav>
    <a href="#">Category 1</a>
    <span>Category 2</span>
    <a href="#" class="sublink-1">Item 2.1</a>
    <span class="sublink-1">Category 2.2</span>
    <a href="#" class="sublink-2">Item 2.2.1</a>
</nav>

<slot />
