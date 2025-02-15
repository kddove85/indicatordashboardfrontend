<template>
  <h2>National Deficit in Billions USD</h2>
  <div v-if="loading">
    <p>Loading...</p>
  </div>
  <div v-else>
    <apexchart :type="type" width="100%" height="300%" :options="chartOptions" :series="series"></apexchart>
  </div>
  <p>Source: The American Presidency Project</p>
</template>

<script>
import { getDeficit } from '../../services/DashboardApi.js';
import { computed, defineComponent, ref, onMounted } from 'vue';
import VueApexCharts from "vue3-apexcharts";

export default defineComponent({
  name: 'Home',
  components: { apexchart: VueApexCharts },
  setup() {
    let data = ref()
    let dataValues = ref([])
    let dataLabels = ref([])
    let loading = ref(true)

    const type = ref("bar");

    onMounted(async() => {
      data.value = await getDeficit();

      dataValues.value = data.value.map(item => item.deficit)
      dataLabels.value = data.value.map(item => item.year)
      loading.value = false;
    })

    let series = computed(() => ([
      {
        name: "Billions of USD",
        data: dataValues.value,
      },
    ]));

    let chartOptions = computed(() => ({
      chart: {
        id: "vuechart-example",
      },
      xaxis: {
        categories: dataLabels.value,
        tickAmount: 20,
      },
      yaxis: {
        title: {
            text: "Billions of USD",
        },
      },
      dataLabels: {
        enabled: false
      },
      fill: {
        opacity: 0.7
      },
      plotOptions: {
        bar: {
          colors: {
            ranges: [{
              from: -10000,
              to: 0,
              color: '#FF0000'
            },
            {
              from: 0,
              to: 10000,
              color: '#388805'
            }]
          }
        },
      },
      annotations: {
          xaxis: [
            {
              x: 1981,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Reagan'
              }
            },
            {
              x: 1989,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Bush'
              }
            },
            {
              x: 1991,
              borderColor: '#50C878',
              label: {
                borderColor: "#50C878",
                style: {
                  color: '#fff',
                  background: "#50C878"
                },
                text: 'Gulf War Ends'
              }
            },
            {
              x: 1992,
              borderColor: '#50C878',
              label: {
                borderColor: "#50C878",
                style: {
                  color: '#fff',
                  background: "#50C878"
                },
                text: 'Cold War Ends'
              }
            },
            {
              x: 1993,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Clinton'
              }
            },
            {
              x: 2001,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Bush'
              }
            },
            {
              x: 2002,
              borderColor: '#50C878',
              label: {
                borderColor: "#50C878",
                style: {
                  color: '#fff',
                  background: "#50C878"
                },
                text: 'Afghan War Starts'
              }
            },
            {
              x: 2008,
              borderColor: '#50C878',
              label: {
                borderColor: "#50C878",
                style: {
                  color: '#fff',
                  background: "#50C878"
                },
                text: 'Housing Crash'
              }
            },
            {
              x: 2009,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Obama'
              }
            },
            {
              x: 2017,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Trump'
              }
            },
            {
              x: 2021,
              borderColor: '#775DD0',
              label: {
                borderColor: "#775DD0",
                style: {
                  color: '#fff',
                  background: "#775DD0"
                },
                text: 'Biden'
              }
            },
          ]
        },
    }));

    return { type, chartOptions, series, loading };
  },
});
</script>