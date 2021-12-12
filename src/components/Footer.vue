<template>
<div>

    <div class="footer-container" :style="{'background-color': mode ? 'rgb(0, 0, 0)': 'rgb(255, 181, 85)'}">
        <a href="https://github.com/jerome0caruso" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
        <a href="https://www.linkedin.com/in/jerome-caruso-42939a200/" target="_blank" title="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
        <a href="mailto:jerome0caruso@gmail.com" target="_blank" title="Email"><i class="far fa-envelope"></i></a>
        <a href="http://jerome0caruso.com" target="_blank" title="Portfolio"><i class="fas fa-briefcase"></i></a>
        <a href="http://myjavascriptprojects.com/resume/JeromeCarusoResume%20(1).pdf" target="_blank" title="Resume"><i class="far fa-file"></i></a>
    </div>
</div>
</template>

 <script>
    export default {
        name: 'Footer',
        props: {
            mode: String
        },
        data() {
            return {
            name: "jerry",
        }
        },
    }

 </script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.footer-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    padding: 3rem 1rem;
    height: auto;
    background-color: rgb(255, 181, 85);
    border: 2px solid white;
    border-top: none;
}
.footer-container a {
    margin: .5rem 1rem;
}
.footer-container i {
    font-size: 3rem;
    color: rgb(127, 193, 196);
}
.footer-container i:hover {
    color: rgb(62, 111, 114);
}

</style>