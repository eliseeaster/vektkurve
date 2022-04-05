<script>
  import { onMount } from "svelte";
  import Chart from "chart.js/auto";

  let ctx;
  let myChart;
  let wanted_weight = [38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48];
  let measured_weight = [37.5, 37.6, 39, 41, 42, 43.2, 42.1, 42.8];
  let reg_date = [
    "07. des 2021",
    "18. des 2021",
    "29. des 2021",
    "09. jan 2022",
    "31. jan 2022",
    "11. feb 2022",
    "05. mar 2022",
    "16 mar 2022",
  ];

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
        labels: reg_date,
        datasets: [
          {
            label: "Ønsket måling",
            data: wanted_weight,
            backgroundColor: "#6490ffa1",
            borderColor: "#6490ff",
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
            data: measured_weight,
            backgroundColor: "rgba(255, 159, 64, 0.2)",
            borderColor: "rgba(255, 159, 64, 1)",
            borderWidth: 1,
            tension: 0.3,
            borderWidth: 5,
            radius: 5,
            pointHoverRadius: 8,
            pointHoverBackgroundColor: "blue",
            //yAxisID: 30,
          },
        ],
      },
      options: {
        scales: {
          y: {
            display: true,
            suggestedMax: 50,
            suggestedMin: 35,
          },

          x: {
            grid: { display: false },
          },
        },
      },
    });
  });
</script>

<canvas id="myChart" width="400" height="150" bind:this={ctx} />

<button on:click={addData(myChart, "30. mar 2022", 44)}>Legg til måling</button>
