<template>
    <div style="border: 1px solid green;">
        <h3>this is {{name}}</h3>
        <button @click="saied">saied</button>
        <div>father saied : {{this.fathersaiedtoson}}</div>
        <div>brother saied:{{brothersaied}}</div>
    </div>
</template>
<script>
import bus from './EventBus';
export default {
    props: {
        fathersaiedtoson: {
            type: String
        }
    },
    inject:['grandson2saidtograndpa'],
    data() {
        return {
            name: 'son2',
            brothersaied: ''
        };
    },
    methods: {
        saied() {
            this.$emit('sonsaiedtofather', 'son2', 'hello im son2');
            this.grandson2saidtograndpa('son2', 'hello im son2');
        }
    },
    beforeMount() {
        // 使用箭头函数 避免this指向bus
        bus.$on('brother2saied', msg => {
            this.brothersaied = msg;
        });
    },
    mounted() {
        bus.$emit('brother1saied', 'brother1 im ready');
    }
}
</script>