# Project
Chartreuse
https://github.com/dainkaplan/Chartreuse

# pie-chart-view-support-various-sizes.patch

BUG: Pie chart does not draw correctly when the size differs from its parent view.
    
This problem occurs because the drawRect method draws using an x and y that is based on
the views center property which returns values in the superviews coordinate system where
the drawRect expects values that are in the views coordinate system.
    
To see this bug in action resize the PieChartView to 100x100 and place it in the top
right corner.