#include <iostream>
#include <vector>
using namespace std;

// Structure to represent a sparse matrix
struct SparseMatrix {
    int row;
    int col;
    int value;
};

// Function to create a sparse matrix from a given 2D array
vector<SparseMatrix> createSparseMatrix(int matrix[][5], int rows, int cols) {
    vector<SparseMatrix> sparseMatrix;
    
    // Iterate through the 2D array to find non-zero elements
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j] != 0) {
                // Store the row index, column index, and value
                SparseMatrix element;
                element.row = i;
                element.col = j;
                element.value = matrix[i][j];
                sparseMatrix.push_back(element);
            }
        }
    }
    return sparseMatrix;
}

// Function to display the sparse matrix representation
void displaySparseMatrix(vector<SparseMatrix> sparseMatrix) {
    cout << "Row\tColumn\tValue\n";
    for (const auto& element : sparseMatrix) {
        cout << element.row << "\t" << element.col << "\t" << element.value << endl;
    }
}

int main() {
    // Example 2D array representing a matrix
    int matrix[4][5] = {
        {0, 0, 3, 0, 4},
        {0, 0, 5, 7, 0},
        {0, 0, 0, 0, 0},
        {0, 2, 6, 0, 0}
    };
    
    int rows = 4; // Number of rows in the matrix
    int cols = 5; // Number of columns in the matrix

    // Create the sparse matrix representation
    vector<SparseMatrix> sparseMatrix = createSparseMatrix(matrix, rows, cols);

    // Display the sparse matrix
    displaySparseMatrix(sparseMatrix);

    return 0;
}
