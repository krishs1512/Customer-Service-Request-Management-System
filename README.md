//Customer Service Request Management System
#include <iostream>
using namespace std;

#define MAX_SIZE 5

class RequestQueue {
private:
    int front, rear;
    int arr[MAX_SIZE];

public:
    RequestQueue() {
        front = -1;
        rear = -1;
    }

    bool isFull() {
        return rear == MAX_SIZE - 1;
    }

    bool isEmpty() {
        return front == -1 || front > rear;
    }

    void addRequest(int requestID) {
        if (isFull()) {
            cout << "Request management system is full. Please try again later." << endl;
            return;
        }
        if (isEmpty()) {
            front = 0;
        }
        rear++;
        arr[rear] = requestID;
        cout << "Request ID " << requestID << " has been added to the queue." << endl;
    }

    void processRequest() {
        if (isEmpty()) {
            cout << "No requests to process." << endl;
            return;
        }
        cout << "Processing request ID " << arr[front] << endl;
        front++;
    }

    void displayQueue() {
        if (isEmpty()) {
            cout << "No requests in the queue." << endl;
            return;
        }
        cout << "Current requests in queue: ";
        for (int i = front; i <= rear; i++) {
            cout << arr[i] << " ";
        }
        cout << endl;
    }
};

int main() {
    RequestQueue rq;
    int choice, requestID;

    while (true) {
        cout << "\nCustomer Service Request Management Menu:\n";
        cout << "1. Add New Request\n";
        cout << "2. Process Request\n";
        cout << "3. Display Queue\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter Request ID to add: ";
                cin >> requestID;
                rq.addRequest(requestID);
                break;
            case 2:
                rq.processRequest();
                break;
            case 3:
                rq.displayQueue();
                break;
            case 4:
                cout << "Exiting..." << endl;
                return 0;
            default:
                cout << "Invalid choice. Please try again." << endl;
                break;
        }
    }

    return 0;
}


