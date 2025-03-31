<script>
  import { onMount } from 'svelte';
  import { page } from '$app/stores';
  import { derived } from 'svelte/store';
  

  const currentHash = derived(page, $page => $page.url.hash);
</script>

<aside>
  <nav>
    <h2>HTML</h2>
    <ul>
      <li><a href="#headings" class:active={$currentHash === '#headings'}>Headings</a></li>
      <li><a href="#forms" class:active={$currentHash === '#forms'}>Forms</a></li>
      <li><a href="#tables" class:active={$currentHash === '#tables'}>Tables</a></li>
      <!-- ... -->
    </ul>

    <h2 class="CSS">CSS</h2>
    <ul>
      <li><a href="#selectors" class:active={$currentHash === '#selectors'}>Selectors</a></li>
      <li><a href="#flexbox" class:active={$currentHash === '#flexbox'}>Flexbox</a></li>
      <!-- ... -->
    </ul>
  </nav>

  <div class="search">
    <input type="text" placeholder="Search..." />
  </div>
</aside>


 

  <style>
    aside {
      width: 300px;
      view-transition-name: Sidebar;
      border-right: 1px solid #ccc;
    }

    nav h2 {
      font-size: 1.5rem;
      margin-bottom: 10px;
      color: var(--HTML-color);
    }

    .active {
      font-weight: bold;
      color: black;
    }

    nav h2.CSS {
      color: var(--CSS-color);
    }
    nav ul {
      list-style-type: none;
      padding: 0;
    }

    nav ul li {
      margin-bottom: 5px;
    }

    nav ul li a {
      text-decoration: none;
      color: #333;
    }

    .search {
      margin-top: 20px;
    }

    .search input {
      width: 80%;
      padding: 8px;
      border-radius: 4px;
      border: 1px solid #ccc;
    }

  </style>
