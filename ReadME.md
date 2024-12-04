# demo

some desciptive text :) !
import matplotlib.pyplot as plt
import numpy as np

# Data for the Pareto chart
categories = [
    "Code Errors", 
    "Requirements Miscommunication", 
    "Testing Oversights", 
    "Integration Issues", 
    "Documentation Errors"
]
defects = [45, 20, 15, 10, 5]
cumulative_percentage = np.cumsum(defects) / sum(defects) * 100

# Create the Pareto chart
fig, ax1 = plt.subplots(figsize=(10, 6))

# Bar chart (defects per category)
bars = ax1.bar(categories, defects, color='skyblue', label='Defects Count')
ax1.set_title("Pareto Analysis: Software Defects", fontsize=14)
ax1.set_xlabel("Defect Categories", fontsize=12)
ax1.set_ylabel("Number of Defects", fontsize=12)
ax1.tick_params(axis='y', labelcolor='blue')
ax1.legend(loc='upper left', fontsize=10)

# Cumulative percentage line
ax2 = ax1.twinx()
ax2.plot(categories, cumulative_percentage, color='red', marker='o', label='Cumulative %')
ax2.set_ylabel("Cumulative Percentage", fontsize=12)
ax2.tick_params(axis='y', labelcolor='red')
ax2.legend(loc='upper right', fontsize=10)

# Add annotations for cumulative percentages
for i, val in enumerate(cumulative_percentage):
    ax2.text(i, val + 2, f"{val:.1f}%", color='red', ha='center')

# Gridlines and layout adjustments
ax1.grid(axis='y', linestyle='--', alpha=0.7)
plt.tight_layout()

# Show the chart
plt.show()
