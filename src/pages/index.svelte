<script>
	import View from "../components/View.svelte"
    export let searchQuery = "";
</script>

<svelte:head>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Hind:wght@300;400;500;600;700&display=swap');
        html, body {
            background-color: #2C2F33;
            font-family: 'Hind', sans-serif;
            text-rendering: optimizeLegibility;
            color: white;
            top: -40px;
        }
        input {
            text-align: center;
            background-color: #36393f;
            color: white;
            border: 4px solid #36393f;
            border-radius: 5px
        }
        input:focus {
            outline: none !important;
            border: 4px solid #3f434a;
        }
    </style>
    <script>
        function load(e, packName, format) {
            e.src = "data:image/png;base64,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";
            e.setAttribute('onClick', "")
            e.onload = ()=>{
                e.parentElement.href = `/pack/${packName.replace(/ /g, "+")}?format=${format}`
                e.src = e.dataset.src;
            }
        }
        //shameless stealing from w3schools
        function setCookie(name,value,days) {
            var expires = "";
            if (days) {
                var date = new Date();
                date.setTime(date.getTime() + (days*24*60*60*1000));
                expires = "; expires=" + date.toUTCString();
            }
            document.cookie = name + "=" + (value || "")  + expires + "; path=/";
        }
        function getCookie(name) {
            var nameEQ = name + "=";
            var ca = document.cookie.split(';');
            for(var i=0;i < ca.length;i++) {
                var c = ca[i];
                while (c.charAt(0)==' ') c = c.substring(1,c.length);
                if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
            }
            return null;
        }

        function highBandwith() {
            if (getCookie('high_bandwith') == "true") {
                setCookie("high_bandwith", false, "1")
                window.location.reload()
            } else {
                setCookie("high_bandwith", true, "1")
                window.location.reload()
            }
        }

        function copy(e, url) {
            navigator.clipboard.writeText(url)
            e.setAttribute('aria-label', 'Copied to your clipboard!'); 
            setTimeout(()=>{
                e.setAttribute('aria-label', 'Click me to copy the URL to your clipboard!')
            }, 3000)
        }
    </script>
    <link rel="stylesheet" href="/css/tooltips.css">
</svelte:head>

<main>
	<h1><a href="https://github.com/discord-stickers/StickerView">Discord Sticker Viewer</a></h1>
	<p>by <a href="https://github.com/respecting">lemons</a> and <a href="https://creatable.cafe">creatable</a></p>
    <span onclick="highBandwith()">toggle high bandwith mode</span><br>
    <input type="text" name="q" placeholder="search for stickers" bind:value={searchQuery}>

	<View {searchQuery} type="pack"/>
</main>
<style>
    main {
        height: 100%;
        text-align: center;
        padding-top: 100px;
        margin: 0 auto;
    }

    a {
        color: white;
    }

    h1 {
        font-weight: 700;
        font-size: 36px;
        line-height: 44px;
        margin: 0;
    }
    
    p {
        color: hsla(0,0%,100%,.6);
        font-size: 16px;
        line-height: 24px;
        margin-top: 12px;
        font-weight: 400;
        margin: 0;
    }

    span {
        cursor: pointer;
    }

    span:hover {
        text-decoration: underline;
    }
</style>