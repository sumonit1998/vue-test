<template>
    <TopBar />

    <nav class="navbar navbar-expand-lg bg-black navbar-dark">
        <div class="container">
            <a class="navbar-brand" href="/"><img width="150px" src="./../assets/images/logo.png" alt=""></a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarText">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                    <a class="nav-link" aria-current="page" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link" href="#">Order Now</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link" href="#">Contact Us</a>
                    </li>
                </ul>
                <span class="navbar-text">
                    <a class="login" href="">Login</a>
                </span>
            </div>
            
        </div>
    </nav>
</template>

<script>
import TopBar from '../components/TopBar.vue';

export default {
    name: 'HeaderView',
    components: {
        TopBar
    }
}
</script>

