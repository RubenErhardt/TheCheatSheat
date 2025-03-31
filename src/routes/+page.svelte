<script>
    import Header from "$lib/Header.svelte";
    import Sidebar from "$lib/Sidebar.svelte";
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
</section>

<style>

    .introduction-thecheatsheet {
        display: flex;
    }

    .introduction-thecheatsheet__text{
        display: flex;
        flex-direction: column;
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
        color: #e44d26;
    }
    .CSS {
        color: #264de4;
    }

    .hero-image{
        padding: 20px;
    }
</style>

