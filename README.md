# test




import { Component } from '@angular/core';

@Component({
  selector: 'app-line-chart',
  templateUrl: './line-chart.component.html',
  styleUrls: ['./line-chart.component.css'],
})
export class LineChartComponent {
  // Line Chart Data
  public lineChartData = {
    datasets: [
      {
        label: 'Sample Data',
        data: Array.from({ length: 100 }, (_, i) => ({ x: i, y: Math.random() * 100 })),
        borderColor: 'rgba(75, 192, 192, 1)',
        borderWidth: 2,
        fill: false,
      },
    ],
  };

  // Line Chart Options
  public lineChartOptions: any = {
    responsive: true,
    scales: {
      x: {
        type: 'linear',
        title: {
          display: true,
          text: 'X Axis',
        },
        ticks: {
          padding: 10, // Adds 10px padding between labels
          callback: function (value, index, ticks) {
            // Optionally, you can limit how many labels to show for readability
            return index % 5 === 0 ? value : '';
          },
        },
      },
      y: {
        title: {
          display: true,
          text: 'Y Axis',
        },
        beginAtZero: true,
        ticks: {
          padding: 10, // Adds 10px padding to Y-axis labels as well
        },
      },
    },
    plugins: {
      legend: {
        display: true,
        position: 'top',
      },
    },
    maintainAspectRatio: false, // Adjust chart size
  };
}
