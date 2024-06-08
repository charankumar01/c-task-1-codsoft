# c-task-1-codsoft
#include <iostream>
#include <vector>
#include <string>

using namespace std;

struct Task {
	string description;
	bool completed;
};

vector<Task> tasks;

void addTask() {
	Task task;
	cout << "Enter a task: ";
	getline(cin, task.description);
	task.completed = false;
	tasks.push_back(task);
}

void viewTasks() {
	cout << "Tasks:" << endl;
	for (int i = 0; i < tasks.size(); i++) {
		cout << i + 1 << ". " << tasks[i].description << " - " << (tasks[i].completed ? "Completed" : "Pending") << endl;
	}
}

void markTaskAsCompleted() {
	int taskNumber;
	cout << "Enter the task number to mark as completed: ";
	cin >> taskNumber;
	if (taskNumber > 0 && taskNumber <= tasks.size()) {
		tasks[taskNumber - 1].completed = true;
	} else {
		cout << "Invalid task number." << endl;
	}
}

void removeTask() {
	int taskNumber;
	cout << "Enter the task number to remove: ";
	cin >> taskNumber;
	if (taskNumber > 0 && taskNumber <= tasks.size()) {
		tasks.erase(tasks.begin() + taskNumber - 1);
	} else {
		cout << "Invalid task number." << endl;
	}
}

int main() {
	while (true) {
		cout << "To-Do List Manager" << endl;
		cout << "-------------------" << endl;
		cout << "1. Add task" << endl;
		cout << "2. View tasks" << endl;
		cout << "3. Mark task as completed" << endl;
		cout << "4. Remove task" << endl;
		cout << "5. Exit" << endl;
		cout << "Enter your choice: ";
		int choice;
		cin >> choice;
		cin.ignore(); // Ignore newline character
		switch (choice) {
			case 1:
				addTask();
				break;
			case 2:
				viewTasks();
				break;
			case 3:
				markTaskAsCompleted();
				break;
			case 4:
				removeTask();
				break;
			case 5:
				return 0;
			default:
				cout << "Invalid choice." << endl;
		}
	}
	return 0;
}

