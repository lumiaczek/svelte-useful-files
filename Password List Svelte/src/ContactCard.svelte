<script>
    export let userName; 
</script>

<div class="contact">
    <header>
        <div>
            <img src="" alt="">
        </div>
        <div class="contact-h">
            <h1>{userName}</h1>
            <h2>Job Title</h2>
        </div>
    </header>
    <div class="content">
        <p>A short discription</p>
    </div>
</div>

<style>
    .contact{
        box-shadow: 0 2px 8px rgba(0,0,0,0.26);
        max-width: 30rem;
        border-radius: 5px;
        margin: 1rem 0;
    }
    header{
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
    }
    .contact-h{
        border-bottom: 1px solid gray;
        width: 100%;
    }
    .contact .content{
        padding: 2rem;
    }

</style>