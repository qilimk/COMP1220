# COMP1220


## 15.6 LAB: Course grade statistics (pandas)

```
import pandas as pd

file_name = input()

# TODO: Read in file_name as a dataframe
grades = pd.read_csv(file_name, sep='\t')

# TODO: Output rows by descending Final scores
print(grades.sort_values(by=['Final'], ascending=False))

print("\nMax Scores:")
# TODO: Output the max scores of each assignment
print((grades.max(numeric_only=True)).to_string())


print("\nMedian Scores:")
# TODO: Output the median scores of each assignment
print((grades.median(numeric_only=True)).to_string())


print("\nAverage Scores:")
# TODO: Output the average scores of each assignment.



print("\nStandard Deviation:")
# TODO: Output the standard devation of each assignment.


```

## 15.7 LAB: Flight status (line plot)

```
import matplotlib.pyplot as plt
import pandas as pd

file = input()


# TODO: Read in the CSV file as a dataframe
flights = pd.read_csv(file)

# TODO: Print the average of flight delays and flight cancellations

print(f"Average delays: {(flights['Delayed'].mean()):.2f}")
print(f"Average cancellations: {(flights['Cancelled'].mean()):.2f}")

# TODO: Create a lineplot of flight delays vs months
plt.plot(flights['Month'], flights['Delayed'], label = 'Delays')


# TODO: In the same figure, create a lineplot of flight cancellations vs months
plt.plot(flights['Month'], flights['Cancelled'], label = 'Cancellations')

# TODO: Add axis labels, title, and legend
plt.xlabel('Months', fontsize = 10)
plt.ylabel('Number of Flights', fontsize = 10)
plt.title('Flight Status at LAX', fontsize = 14)
plt.legend()

# Save figure as output_fig.png
plt.savefig('output_fig.png')
```
