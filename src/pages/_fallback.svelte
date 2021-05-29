<svelte:head>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Hind:wght@300;400;500;600;700&display=swap');
        html, body {
            background-color: #2C2F33;
            font-family: 'Hind', sans-serif;
            text-rendering: optimizeLegibility;
            color: white;
        }
    </style>
</svelte:head>

<main>
	<h1>not found.</h1>
    <br>
    <span onclick="history.back()">go back</span>
</main>

<style>
    main {
        height: 100%;
        text-align: center;
        padding-top: 100px;
        margin: 0 auto;
    }

    h1 {
        font-weight: 700;
        font-size: 72px;
        line-height: 44px;
        margin: 0;
    }
    
    span {
        cursor: pointer;
    }

    span:hover {
        text-decoration: underline;
    }
</style>