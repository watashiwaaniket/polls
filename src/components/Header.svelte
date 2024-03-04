<header>
    <h1>
        <!-- <img src="\img\logoPolls.png" alt="Poll Ninja Logo"> -->
        P
        <span class="loader"></span>
        LLs
    </h1>
</header>

<style>
    header{
        background: #45c496;
        padding: 20px;
    }
    h1{
        color: #FFF;
        margin: 0;
        display:flex;
        justify-content: center;
        align-items: center;
        font-size: 60px;
    }
    /* img{

        max-width: 120px;
    } */
    .loader {
        display: block;
        width: 84px;
        height: 84px;
        position: relative;
    }

    .loader:before , .loader:after {
        content: "";
        position: absolute;
        left: 50%;
        bottom: 0;
        width: 64px;
        height: 64px;
        border-radius: 50%;
        background: #FFF;
        transform: translate(-50% , -100%)  scale(0);
        animation: push_401 2s infinite linear;
    }

    .loader:after {
        animation-delay: 1s;
    }

    @keyframes push_401 {
    0% , 50% {
        transform: translate(-50% , 0%)  scale(1)
    }

    100% {
        transform: translate(-50%, -100%) scale(0)
    }
}

</style>