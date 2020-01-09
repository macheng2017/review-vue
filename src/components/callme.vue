<template>
    <div>
        <button v-on:click="boost">callme</button>
    </div>

</template>

<script>
    export default {
        name: "callme",
        data() {
            return {
                message: 'hello world'
            }
        },
        created() {
            // 先注册一个事件,等待被emit
            this.$on('my_event', this.handleEvent)
            this.$on('my_event', this.handleEvent2)
        },
        methods: {
            handleEvent(e) {
                // eslint-disable-next-line no-console
                console.log(this.message, e)
            },
            handleEvent2(e) {
                // eslint-disable-next-line no-console
                console.log(this.message, e)
            },
            boost() {
                this.$emit('my_event', 'my params')
            }
        }
    }
</script>

<style scoped>

</style>
