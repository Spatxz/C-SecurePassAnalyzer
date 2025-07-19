# C-SecurePassAnalyzer
A simple yet effective C++ program that evaluates the strength of a password based on common security criteria. Useful for beginners learning about strings, conditions, and input handling in C++.


#include <iostream>
#include <string>
#include <cctype>

using namespace std;

int checkStrength(const string& password) {
    bool hasLower = false, hasUpper = false, hasDigit = false, hasSymbol = false;
    int score = 0;

    for (char ch : password) {
        if (islower(ch)) hasLower = true;
        else if (isupper(ch)) hasUpper = true;
        else if (isdigit(ch)) hasDigit = true;
        else hasSymbol = true;
    }

    if (password.length() >= 8) score += 2;
    else if (password.length() >= 5) score += 1;

    if (hasLower) score++;
    if (hasUpper) score++;
    if (hasDigit) score++;
    if (hasSymbol) score++;

    return score;
}

string getStrengthLabel(int score) {
    if (score >= 6) return "Very Strong 💪";
    else if (score >= 5) return "Strong ✅";
    else if (score >= 3) return "Medium ⚠️";
    else return "Weak ❌";
}

int main() {
    string password;

    cout << "Enter your password: ";
    cin >> password;

    int score = checkStrength(password);
    string label = getStrengthLabel(score);

    cout << "Password Strength: " << label << endl;

    return 0;
}
