<template>
    <div>
        <canvas id="myChart"></canvas>
    </div>
</template>

<script setup>
import Chart from 'chart.js/auto';

const labels=[
    'january',
    'february',
    'march',
    'april',
    'may',
    'june',
];

const data= {
    labels : labels,
    datasets: [{
        label: 'Pengunjung',
        backgroundColor: 'rgb(255, 99, 132)',
        borderColor: 'rgb(255, 99, 132)',
        data: [0, 10, 5, 2, 20, 30, 45],
    }]
};

const config = {
    type: 'bar',
    data: data,
    options: {}
};

onMounted(()=>{
    const myChart = new Chart(
    document.getElementById('myChart'),
    config
);
})
</script>