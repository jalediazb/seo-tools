<template>
    <div id="app" class="has-background-light" style="min-height: 100vh">
        <section class="section">
            <div class="container snippet-container">
                <div class="columns is-multiline">
                    <Snippets></Snippets>
                </div>
            </div>
        </section>
        <!-- <HelloWorld msg="Hello Vue in CodeSandbox!" /> -->
    </div>
</template>
<script>
//import HelloWorld from "./components/HelloWorld";
import Snippets from "./components/Snippets.vue";
import 'bulma/css/bulma.css'

export default {
    name: "App",
    components: {
        // HelloWorld,
        Snippets,
    },
};
</script>
<style>
#app {}
.snippet-container {
	max-width: 648px !important;
}
</style>
