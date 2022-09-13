<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        .chartBox{
            width: 600px;
            padding: 20px;
        }

    </style>
</head>
<body>
    <div class="chartBox">
        <canvas id="myChart"></canvas>
    </div>
    <div class="selectBox">
        <select id="coffeesales">
            <option value="12, 19, 3, 5, 2, 3">coffee</option>
            <option value="11, 18, 9, 10, 9, 10">tea</option>
            <option value="23, 37, 12, 15, 11, 13">both</option>
        </select>
    </div>


    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <script>
    const ctx = document.getElementById('myChart').getContext('2d');
    const myChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
            datasets: [{
                label: 'pavan',
                data: [12, 19, 3, 5, 2, 3],
                backgroundColor: [
                    'rgba(255, 99, 132, 0.2)',
                    'rgba(54, 162, 235, 0.2)',
                    'rgba(255, 206, 86, 0.2)',
                    'rgba(75, 192, 192, 0.2)',
                    'rgba(153, 102, 255, 0.2)',
                    'rgba(255, 159, 64, 0.2)'
                ],
                borderColor: [
                    'rgba(255, 99, 132, 1)',
                    'rgba(54, 162, 235, 1)',
                    'rgba(255, 206, 86, 1)',
                    'rgba(75, 192, 192, 1)',
                    'rgba(153, 102, 255, 1)',
                    'rgba(255, 159, 64, 1)'
                ],
                borderWidth: 1
            }]
        },
        options: {
            scales: {
                y: {
                    beginAtZero: true
                }
            }
        }
    });

    const coffeesales = document.getElementById('coffeesales');
    coffeesales.addEventListener('change',salesTracker);
    function salesTracker(){
        const label = coffeesales.options[coffeesales.selectedIndex].text;
        myChart.data.datasets[0].label = label;
        myChart.data.datasets[0].data = coffeesales.value.split(',');
        myChart.update();
    }





    </script>

</body>
</html>
