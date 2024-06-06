<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/pengunjung/tambah">
                    <div class="card bg-pengunjung rounded-5">
                        <div class="card-body">
                            <h2>Pengunjung</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-6">
                <nuxt-link to="/buku">
                    <div class="card bg-buku rounded-5">
                        <div class="card-body">
                            <h2>Cari Buku</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
    </div>
    <h2 style="margin: 30px;"><strong>STATISTIK</strong></h2>
    <div class="container-fluid">
        <div class="row justify-content-evenly rounded-3">
            <div class="col-5">
                <div class="card1">
                    <div class="yuli">
                        <h2>{{ totalPengunjung }} Pengunjung</h2>
                    </div>
                </div>
            </div>
            <div class="col-5">
                <div class="yuli1">
                    <h2>{{ totalBuku }} Buku</h2>
                </div>
            </div>
        </div>
    </div>
    <div class="line">
        <Statistik />
    </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const totalPengunjung = ref(0)

async function getTotalPengunjung() {
    const { count, error } = await supabase
        .from('pengunjung')
        .select('*', { count: 'exact', head: true })
    if (error) throw error
    if (count) totalPengunjung.value = count
}
const totalBuku = ref(0)

async function getTotalBuku() {
    const { count, error } = await supabase
        .from('buku')
        .select('*', { count: 'exact', head: true })
    if (error) throw error
    if (count) totalBuku.value = count
}

onMounted(() => {
    getTotalPengunjung()
    getTotalBuku()
    
    
})
</script>

<style scoped>
.v2 {
    height: 3px;
    width: 98%;
    margin-left: 30px;
    border-left: 3px solid black;
    background-color: black;
}

.v1 {
    margin-top: 40px;
    margin-left: 30px;
    border-left: 3px solid black;
    height: 400px;
}

.card {
    height: 200px;
    box-shadow: 1px 1px 5px #424242;
}

.card.bg-pengunjung {
    background-image: url('../assets/img/kunjungan.png');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}

.card.bg-buku {
    background: url('../assets/img/cari buku.png') no-repeat center center;
    background-size: cover;
}

.yuli {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #E4CA6B;
}

.yuli1 {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #1DDD81;
}
</style>