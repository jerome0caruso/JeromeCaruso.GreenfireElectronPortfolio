<template>
<div>

    <div class="footer-container">
        <a href="https://github.com/jerome0caruso" target="_blank"><i class="fab fa-github"></i></a>
        <a href="http://jerome0caruso.com" target="_blank"><i class="fab fa-linkedin-in"></i></a>
        <a href="mailto:jerome0caruso@gmail.com" target="_blank">Email</a>
        <a href="http://jerome0caruso.com" target="_blank">Portfolio</a>
        <a href="http://myjavascriptprojects.com/resume/JeromeCarusoResume%20(1).pdf" target="_blank">Resume</a>
    </div>
</div>
</template>

 <script>
    export default {
        name: 'Footer',
        props: {
            
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
</style>