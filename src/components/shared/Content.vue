<template>
    <div class="main-content">
        <aside v-if="$slots.nav" class="content-navigation">
            <slot name="nav"></slot>
        </aside>
        <section v-if="$slots.info" class="content-info">
            <slot name="info"></slot>
        </section>
    </div>
</template>

<script>
    export default {
        name: 'Content',
        data: function() {
            return {

            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
