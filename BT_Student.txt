// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentRegistry {
    // Structure to represent a student
    struct Student {
        uint256 id;
        string name;
        uint256 age;
    }

    // Array to store the list of students
    Student[] public students;

    // Function to add a new student
    function addStudent(uint256 _id, string memory _name, uint256 _age) public {
        // Creating a new instance of the Student structure
        Student memory newStudent = Student(_id, _name, _age);
        
        // Adding the new student to the array
        students.push(newStudent);
    }

    // Function to get the details of a specific student by index
    function getStudent(uint256 index) public view returns (uint256, string memory, uint256) {
        require(index < students.length, "Index out of bounds");
        
        // Returning the details of the student at the given index
        return (students[index].id, students[index].name, students[index].age);
    }

    // Function to get the total number of students
    function getStudentCount() public view returns (uint256) {
        // Returning the length of the students array
        return students.length;
    }
}
