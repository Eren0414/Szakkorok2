<template>
    <div class="card">
        <div class="card-header">
            <div class="card-body">{{ szakkor.nev }}</div>
                <span class="my-span" v-for="(diak, i) in szakkorTanulok" :key="diak.id">
                    {{ diak.nev }}<span v-if="i < szakkorTanulok.length - 1">, </span>
                </span>
            </div>
    </div>
</template>

<script>
export default {
    props: [
        "szakkor",
        "diakok"
    ],
    computed: {
        szakkorTanulok() {
            return this.diakok
            .filter((d) => d.szakkorId == this.szakkor.id)
            .sort((a, b) => a.nev.localeCompare(b.nev))
        }
    }
}
</script>

<style>
.my-span {
    color: darkslategrey;
}

.card-body{
    border: 2px solid;
}
</style>