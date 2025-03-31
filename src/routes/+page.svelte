<script>
    import { page } from '$app/stores';
    import { onMount } from 'svelte';
    import { writable, derived } from 'svelte/store';
    import Header from '$lib/Header.svelte';
    import Sidebar from '$lib/Sidebar.svelte';
    import { onNavigate } from '$app/navigation';

onNavigate((navigation) => {
	if (!document.startViewTransition) return;

	return new Promise((resolve) => {
		document.startViewTransition(async () => {
			resolve();
			await navigation.complete;
		});
	});
});

  
    const currentHash = derived(page, $page => $page.url.hash || '#headings');
  
    const componentMap = {
      '#headings': () => import('$lib/Headings.svelte'),
      '#forms': () => import('$lib/Forms.svelte'),
    };
  
    const Component = writable(null);
  
    $: if ($currentHash && componentMap[$currentHash]) {
      componentMap[$currentHash]().then(mod => {
        Component.set(mod.default);
      });
    } else {
      Component.set(null); // fallback
    }
  </script>
  

<Header/>

<section class="introduction-thecheatsheet">
    <div class="introduction-thecheatsheet__text">
    <h1 class="introduction-thecheatsheet__title">A visual <span class="HTML">HTML</span> & <span class="CSS">CSS</span> cheatsheet built within Sveltekit</h1>
    <p class="introduction-thecheatsheet__description">
        Explore a collection of <span class="HTML">HTML</span> and <span class="CSS">CSS</span> snippets, organized by category, to help you quickly find the code you need.
        Each snippet is accompanied by a live demo, allowing you to see the code in action and understand how it works.
        Whether you're a beginner or an experienced developer, this cheatsheet is a valuable resource for anyone looking to improve their <span class="HTML">HTML</span> and <span class="CSS">CSS</span> skills.
    </p>
    <p class="introduction-thecheatsheet__description__note">
        This project is a work in progress, and we welcome contributions from the community.
    </p>
</div>
    <div class="hero-image">
        <img src="/imgs/1_lJ32Bl-lHWmNMUSiSq17gQ.png" alt="HTML & CSS">
    </div>
</section>

<section class="content-html-css">
    <Sidebar/>
    <div class="main-content">
        {#if $Component}
          <svelte:component this={$Component} />
        {:else}
          <p>Section not found or not loaded yet.</p>
        {/if}
      </div>

</section>

<style>

    .introduction-thecheatsheet {
        display: flex;
        margin-bottom: 2rem;
    }

    .introduction-thecheatsheet__text{
        display: flex;
        flex-direction: column;
        max-width: 750px;
    }

    .introduction-thecheatsheet__title {
        font-size: 2.5rem;
        margin-bottom: 1rem;
    }
    .introduction-thecheatsheet__description {
        font-size: 1.2rem;
        margin-bottom: 1rem;
        font-style: italic;
    }

    .introduction-thecheatsheet__description__note {
       font-weight: bold;

    }

    .HTML {
        color: var(--HTML-color);
    }
    .CSS {
        color: var(--CSS-color);
    }

    .hero-image{
        padding: 1rem 1rem;
    }

    .content-html-css {
        display: flex;
        margin-top: 2rem;
    }

    .main-content {
        margin-left: 1rem;
    }

    @keyframes fade-in {
	from {
		opacity: 0;
	}
}

@keyframes fade-out {
	to {
		opacity: 0;
	}
}

@keyframes slide-from-right {
	from {
		transform: translateX(30px);
	}
}

@keyframes slide-to-left {
	to {
		transform: translateX(-30px);
	}
}

:root::view-transition-old(root) {
	animation:
		90ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
		300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
}

:root::view-transition-new(root) {
	animation:
		210ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
		300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
}

</style>

