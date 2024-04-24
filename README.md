# COMP1220


## 12.11 LAB: Course Grade

```
def grader(score):
    if score >= 90:
        return 'A'
    elif score >= 80:
        return 'B'
    elif score >= 70:
        return 'C'
    elif score >= 60:
        return 'D'
    else:
        return 'F'

file_name = input("Enter the file name: ")

# Initialize data structures for storing exam scores
midterm1_scores = []
midterm2_scores = []
final_scores = []
students_info = []

with open(file_name, 'r') as file:
    for line in file:
        if line.strip():  # Ensure that the line is not empty
            parts = line.strip().split('\t')
            last_name = parts[0]
            first_name = parts[1]
            midterm1 = int(parts[2])
            midterm2 = int(parts[3])
            final = int(parts[4])

            # Compute the average score
            average = (midterm1 + midterm2 + final) / 3
            grade = grader(average)

            # Store scores for averages calculation
            midterm1_scores.append(midterm1)
            midterm2_scores.append(midterm2)
            final_scores.append(final)

            # Store student information
            students_info.append((last_name, first_name, midterm1, midterm2, final, grade)) 

avg_midterm1 = sum(midterm1_scores) / len(midterm1_scores)
avg_midterm2 = sum(midterm2_scores) / len(midterm2_scores)
avg_final = sum(final_scores) / len(final_scores)

# Write to the report file
with open('report.txt', 'w') as report:
    for info in students_info:
        report.write(f"{info[0]}\t{info[1]}\t{info[2]}\t{info[3]}\t{info[4]}\t{info[5]}")
    report.write(f"Averages: midterm1 {avg_midterm1:.2f}, midterm2 {avg_midterm2:.2f}, final {avg_final:.2f}\n")

```

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
