<template>
    <div class="legend">
        <div class="item" v-for="item in items" :key="item.id" :style="item.highlight ? {opacity: '1'} : {opacity: '0.3'}">
            <div class="example" :style="{background: item.color}"></div>
            <p class="text" >
                {{ item.name }}
            </p>
            <div v-if="item.highlight" class="underline" :style="{background: item.color}"></div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Legend',
    props: {
        items: {
            default: [{id: 0, name: 'item 1', color: 'black', highlight: false}]
        }
    }
}
</script>

<style scoped>
.item {
    position: relative;
    display: flex;
    margin-bottom: 16px;
}
.example {
    margin-right: 13px;
    width: 14px;
    height: 14px;
}
.text {
    position: relative;
    padding: 0;
    margin: 0;
    width: 162px;
    color:black;
    text-transform: uppercase;
}
.underline {
    position: absolute;
    bottom: 0;
    left: 26px;
    width: 162px;
    height: 1px;
}
</style>