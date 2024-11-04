To create a list of students who have submitted their assignments, we can use an array to store the names in the order of submission. Each time a student submits their assignment, their name can be added to the next available position in the array. Since the number of students might be known in advance, we can use a fixed-size array. In this example, we’ll assume a maximum of 50 students can submit assignments.

Steps:
1.Define an Array: We'll define an array to hold up to 50 student names.
2.Insert Names in Order of Submission: When a student submits their assignment, we add their name to the next position in the array.
3.Display the List of Submitted Students: After adding names, we can display the list to show the order of submissions.

#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 50
#define MAX_NAME_LENGTH 100

int main() {
   
    char students[MAX_STUDENTS][MAX_NAME_LENGTH];  // Array to hold student names
    int count = 0;  // Variable to keep track of the number of students who submitted

    char name[MAX_NAME_LENGTH];
    int choice;

    printf("Student Assignment Submission Tracker\n");

    // Loop to allow the teacher to keep adding students
    while (1) {
        printf("\n1. Add Student Submission\n");
        printf("2. Display Submitted Students\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                if (count < MAX_STUDENTS) {
                    printf("Enter student's name: ");
                    scanf(" %[^\n]", name);  // Read the student name with spaces
                    strcpy(students[count], name);  // Copy name into the students array
                    count++;
                    printf("Student '%s' has been added to the list.\n", name);
                } else {
                    printf("Maximum number of students reached. Cannot add more.\n");
                }
                break;

            case 2:
                printf("\nList of Students who submitted assignments:\n");
                if (count == 0) {
                    printf("No submissions yet.\n");
                } else {
                    for (int i = 0; i < count; i++) {
                        printf("%d. %s\n", i + 1, students[i]);
                    }
                }
                break;

            case 3:
                printf("Exiting...\n");
                return 0;

            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}

Explanation
1.Array Declaration: We declare a 2D array students with MAX_STUDENTS rows and MAX_NAME_LENGTH columns. Each row holds a student's name.
2.Count Variable: We maintain a count variable to keep track of how many students have submitted assignments.
3.Main Menu Loop:
a.Option 1 (Add Student Submission): This allows the teacher to add a new student’s name to the array if there’s space. The name is copied into the next position in the students array, and count is incremented.
b.Option 2 (Display Submitted Students): This displays the list of all submitted students in the order they were added.
c.Option 3 (Exit): Exits the program.
