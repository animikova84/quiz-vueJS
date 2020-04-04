<template>
    <div class="navigation">
        <ul>
            <li v-for="(item, i) in navItems" :key="item.id">
                <a :class="{ active: i === selectedNavigation }" @click="navItemClickEvent(i)">{{ item.name }}</a>
            </li>
        </ul>

        <ul>
            <li>
                <a href="#">Add quiz game</a>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        props: {
            navItems: {
                type: Array,
                required: true,
            },
            selectedNavigation: {
                type: Number,
                required: true
            }
        },
        methods: {
            navItemClickEvent(ind) {
                this.$emit('navigate', ind);
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
