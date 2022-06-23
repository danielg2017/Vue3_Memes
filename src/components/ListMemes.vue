<template>
    <h1>{{ title }}</h1>
    <div class="total-show">
        <select @change="changeTotalShow">
            <option value="">All</option>
            <option value="4">4</option>
            <option value="12">12</option>
            <option value="20">20</option>
        </select>
    </div>
    <div class="row">
        <template v-for="meme in memes" :key="meme.id">
            <Meme :meme="meme" />
        </template>
    </div>
</template>

<script>
import { useStore } from "vuex";
import { onMounted, computed } from "vue";
import Meme from "./Meme.vue";
export default {
    components: {
        Meme,
    },

    setup() {
        const store = useStore();
        const memes = computed(() => store.state.memes);

        onMounted(() => {
            store.dispatch("getMemes");
        });

        const changeTotalShow = (event) => {
            store.dispatch("getMemes", {
                total: event.target.value,
            });
        };
        return {
            title: store.state.titleApp,
            memes,
            changeTotalShow,
        };
    },
};
</script>

<style scoped>
h1 {
    text-align: center;
}
.total-show {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 5px;
}
</style>
