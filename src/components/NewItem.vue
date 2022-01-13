<template>
<tr>
    <td><input type="text" v-model="nev"></td>
    <td><input type="text" v-model="kiadasi_ev"></td>
    <td><input type="text" v-model="kiado"></td>
    <td><input type="text" v-model="free_to_play"></td>
    <td><button @click="Add">Add</button></td>
</tr>
</template>

<script>
export default {
    props: ['new'],
    data() {
        return {
            nev: this.new.nev,
            kiadasi_ev: this.new.kiadasi_ev,
            kiado: this.new.kiado,
            free_to_play:this.new.free_to_play
        }
    },
    methods: {
        Add() {
            this.$emit('post-new', {
                new: {
                    nev: this.nev,
                    kiadasi_ev: this.kiadasi_ev,
                    kiado: this.kiado,
                    free_to_play:this.free_to_play
                    },
            })
            this.nev="",
            this.kiadasi_ev="",
            this.kiado=""
            this.free_to_play=""
        }
    }
}
</script>

<style>
</style>