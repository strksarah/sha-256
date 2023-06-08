#include <iostream>
#include <string>
#include <unordered_map>
#include <functional>
using namespace std;

string sha256(const string& str) {
    hash<string> hasher;
    return to_string(hasher(str));
}

bool isPasswordValid(const string& password) {
    return password.length() >= 8;
}
bool signUp(unordered_map<string, string>& users) {
    string username, password;
    cout << "Sign Up\n";
    cout << "Username: ";
    cin >> username;
    if (users.find(username) != users.end()) {
        cout << "Polzovatel uzhe sushestvuet\n";
        return false;
    }
    cout << "Password: ";
    cin >> password;
    if (isPasswordValid(password)) {
        string hashedPassword = sha256(password);
        users[username] = hashedPassword;
        cout << "Account sozdan uspeshno!\n";
        return true;
    } else {
        cout << "Invalid password! Password dolzhen byt at least 8 symbolov long.\n";
        return false;
    }
}
bool signIn(const unordered_map<string, string>& users) {
    string username, password;
    cout << "Sign In\n";
    cout << "Username: ";
    cin >> username;
    auto it = users.find(username);
    if (it == users.end()) {
        cout << "Polzovatel not sushestvuet\n";
        return false;
    }
    cout << "Password: ";
    cin >> password;
    string hashedPassword = sha256(password);
    if (hashedPassword == it->second) {
        cout << "Vhod proshel uspeshno!\n";
        return true;
    } else {
        cout << "Invalid password!\n";
        return false;
    }
}
int main() {
    unordered_map<string, string> users;
    int choice;
    bool isLoggedIn = false;
    while (!isLoggedIn) {
        cout << "Welcome!\n";
        cout << "1. Sign Up\n";
        cout << "2. Sign In\n";
        cout << "Select an option: ";
        cin >> choice;
        switch (choice) {
            case 1:
                signUp(users);
                break;
            case 2:
                isLoggedIn = signIn(users);
                break;
                return 0;
            default:
                cout << "Invalid choice!\n";
        }

        cout << endl;
    }
    return 0;
}
