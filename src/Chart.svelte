<script>
  import { onMount } from "svelte";
  import Chart from "chart.js/auto";

  let ctx;
  let myChart;
  let chartData = [12, 19, 3, 5, 2, 3];
  let chartData2 = [1, 2, 3, 4, 5, 6];
  let labels = ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"];

  let data = {
    labels: ["Uke1", "Uke2", "Uke3", "Uke4", "Uke5"],
    datasets: [
      {
        values: [43, 43.4, 44, 45, 45.5],
      },
    ],
  };

  function addData(chart, label, data) {
    chart.data.labels.push(label);
    chart.data.datasets.forEach((dataset) => {
      dataset.data.push(data);
    });
    chart.update();
  }

  onMount(async () => {
    myChart = new Chart(ctx, {
      type: "line",
      data: {
        labels: labels,
        datasets: [
          {
            label: "Ønsket måling",
            data: chartData,
            backgroundColor: "rgba(255, 159, 64, 0.2)",
            borderColor: "rgba(255, 159, 64, 1)",
            borderWidth: 1,
            tension: 0.3,
            borderWidth: 5,
            radius: 5,
            pointHoverRadius: 8,
            pointHoverBackgroundColor: "blue",
            // fill: true,
            // backgroundColor: "#ffad4e94",
          },
          {
            label: "Faktisk måling",
            data: chartData2,
            backgroundColor: "rgba(255, 159, 64, 0.2)",
            borderColor: "rgba(255, 159, 64, 1)",
            borderWidth: 1,
            tension: 0.3,
            borderWidth: 5,
            radius: 5,
            pointHoverRadius: 8,
            pointHoverBackgroundColor: "blue",
          },
        ],
      },
      options: {
        scales: {
          y: {
            beginAtZero: true,
          },
          x: {
            grid: { display: false },
          },
        },
      },
    });
  });
</script>

<canvas id="myChart" width="400" height="100" bind:this={ctx} />

<button on:click={addData(myChart, "Uke2", 44)}>Legg til måling</button>
