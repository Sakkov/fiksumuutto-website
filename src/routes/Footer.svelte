<script lang="ts">
    import muutos from '$lib/Images/muutospainoaineisto.svg';
    import pohjolanpolte from '$lib/Images/pohjolanpolte.png';
    import kovanenio from '$lib/Images/kovanenio.png';
</script>

<footer>
    <div class="yhteistyossa">
        <h2 style="color: black">
            Yhteistyössä:
        </h2>
        <a href="https://muutoslkv.fi/henri-niskala/">
            <img src={muutos} alt="Muutos Henri Niskala">
        </a>
        <a href="https://pohjolanpolte.fi/">
            <img src="{pohjolanpolte}" alt="Pohjolanpolte">
        </a>
        <a href="https://kovanen.io/">
            <img src="{kovanenio}" alt="Kovanen.io">
        </a>
    </div>
    <div class="footer-cc">
        © 2024 Fiksu Kuljetus Oy | y-tunnus: <a href="https://tietopalvelu.ytj.fi/yritys/3299698-1" target="_blank">3299698-1</a> | <a href="/policy">Tietosuojaseloste</a> | Nettisivut tehnyt <a href="https://kovanen.io">kovanen.io</a>
    </div>
</footer>

<style>

    .yhteistyossa {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        margin: 20px 0;
    }

    .yhteistyossa h2 {
        width: 100%;
        margin: 20px 0;
    }

    .yhteistyossa a {
        text-decoration: none;
        width: 400px;
        display: block;
    }

    img {
        max-height: 200px;
        width: auto;
        margin: 10px auto;
    }
</style>