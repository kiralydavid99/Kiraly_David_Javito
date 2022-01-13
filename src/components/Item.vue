<template>
<tr>
    <td v-if="!edit">{{post.nev}}</td>
    <td v-if="!edit">{{post.kiadasi_ev}}</td>
    <td v-if="!edit">{{post.kiado}}</td>
    <td v-if="!edit">{{post.free_to_play}}</td>

    <td v-if="!edit">
        <button @click="Edit">Edit</button>
        <button @click="Delete">X</button>
    </td>
    

    <td v-if="edit"><input type="text" v-bind="nev" v-model="nev"></td>
    <td v-if="edit"><input type="text" v-bind="kiadasi_ev" v-model="kiadasi_ev"></td>
    <td v-if="edit"><input type="text" v-bind="kiado" v-model="kiado"></td>
    <td v-if="edit"><input type="text" v-bind="kiado" v-model="free_to_play"></td>

    <td v-if="edit"><button @click="Save">Save</button></td>
</tr>
</template>

<script>
export default {
    props: ['post'],
    data() {
        return {
            nev: this.post.nev,
            kiadasi_ev: this.post.kiadasi_ev,
            kiado: this.post.kiado,
            free_to_play:this.post.free_to_play,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('post-row-changed', {
                original: this.post,
                new: {
                    nev: this.nev,
                    kiadasi_ev: this.kiadasi_ev,
                    kiado: this.kiado,
                    free_to_play:this.free_to_play
                    },
            })
        },
        Delete(){
            this.$emit('post-row-delete',{
                original:this.row
            })
        }
    }
}
</script>

<style>
</style>