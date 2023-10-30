


#include <iostream>
#include <string>

const int MAX_STUDENTS = 100;

// Function to calculate the overall grade
double calculateGrade(double assignmentScore, double quizScore, double examScore,
                      double assignmentWeight, double quizWeight, double examWeight) {
    double totalWeight = assignmentWeight + quizWeight + examWeight;
    return (assignmentScore * assignmentWeight + quizScore * quizWeight + examScore * examWeight) / totalWeight;
}

// Function to map numerical grade to a letter grade
std::string mapToLetterGrade(double numericalGrade) {
    if (numericalGrade >= 90) {
        return "A";
    } else if (numericalGrade >= 80) {
        return "B";
    } else if (numericalGrade >= 70) {
        return "C";
    } else if (numericalGrade >= 60) {
        return "D";
    } else {
        return "F";
    }
}

int main() {
    std::string names[MAX_STUDENTS];
    int ids[MAX_STUDENTS];
    double assignmentScores[MAX_STUDENTS], quizScores[MAX_STUDENTS], examScores[MAX_STUDENTS];
    double assignmentWeight, quizWeight, examWeight;

    int numStudents;

    std::cout << "Enter the number of students: ";
    std::cin >> numStudents;

    for (int i = 0; i < numStudents; ++i) {
        std::string name;
        int id;
        double assignmentScore, quizScore, examScore;

        std::cout << "Enter student name: ";
        std::cin >> name;
        names[i] = name;

        std::cout << "Enter student ID: ";
        std::cin >> id;
        ids[i] = id;

        std::cout << "Enter assignment score: ";
        std::cin >> assignmentScore;
        assignmentScores[i] = assignmentScore;

        std::cout << "Enter quiz score: ";
        std::cin >> quizScore;
        quizScores[i] = quizScore;

        std::cout << "Enter exam score: ";
        std::cin >> examScore;
        examScores[i] = examScore;
    }

    std::cout << "Enter the weightage for assignments, quizzes, and exams (e.g., 0.3 0.3 0.4): ";
    std::cin >> assignmentWeight >> quizWeight >> examWeight;

    for (int i = 0; i < numStudents; ++i) {
        double overallGrade = calculateGrade(assignmentScores[i], quizScores[i], examScores[i], assignmentWeight, quizWeight, examWeight);
        std::string letterGrade = mapToLetterGrade(overallGrade);

        std::cout << "Student: " << names[i] << " (ID: " << ids[i] << ")\n";
        std::cout << "Overall Grade: " << overallGrade << " (Letter Grade: " << letterGrade << ")\n";
    }

    return 0;
}
