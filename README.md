# Prodigy-InfoTech-task-03
This program defines criteria for assessing the strength of a password, including length, presence of uppercase and lowercase letters, numbers, and special characters. It then checks these criteria against the provided password and returns feedback on its strength.

import re

def assess_password_strength(password):
    score = 0
    
    # Criteria 1: Length
    if len(password) >= 8:
        score += 1
    if len(password) >= 12:
        score += 1
    
    # Criteria 2: Presence of uppercase and lowercase letters
    if re.search("[A-Z]", password) and re.search("[a-z]", password):
        score += 1
    
    # Criteria 3: Presence of numbers
    if re.search("[0-9]", password):
        score += 1
    
    # Criteria 4: Presence of special characters
    if re.search("[!@#$%^&*(),.?\":{}|<>]", password):
        score += 1
    
    # Assess password strength based on the score
    if score == 0:
        return "Very Weak"
    elif score == 1:
        return "Weak"
    elif score == 2:
        return "Moderate"
    elif score == 3:
        return "Strong"
    elif score == 4:
        return "Very Strong"
    else:
        return "Unknown"

def main():
    while True:
        password = input("Enter your password: ")
        if password.lower() == 'exit':
            break
        strength = assess_password_strength(password)
        print(f"Password strength: {strength}")

if __name__ == "__main__":
    main()

