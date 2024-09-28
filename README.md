# CODSOFT_TASK03
import random
import string

def generate_password(length, complexity, include_uppercase, include_numbers, include_special_chars):
    characters = string.ascii_lowercase

    if include_uppercase:
        characters += string.ascii_uppercase
    if include_numbers:
        characters += string.digits
    if include_special_chars:
        characters += string.punctuation

    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def password_generator():
    print("Password Generator")
    print("1. Weak (only lowercase letters)")
    print("2. Medium (letters, uppercase and lowercase)")
    print("3. Strong (letters, uppercase and lowercase, digits, and special characters)")

    complexity_choice = input("Enter your choice (1/2/3): ")

    if complexity_choice in ['1', '2', '3']:
        if complexity_choice == '1':
            complexity = 'weak'
            include_uppercase = False
            include_numbers = False
            include_special_chars = False
        elif complexity_choice == '2':
            complexity = 'medium'
            include_uppercase = True
            include_numbers = False
            include_special_chars = False
        elif complexity_choice == '3':
            complexity = 'strong'
            include_uppercase = True
            include_numbers = True
            include_special_chars = True

        length = int(input("Enter the desired length of the password: "))

        password = generate_password(length, complexity, include_uppercase, include_numbers, include_special_chars)
        print(f"Generated Password: {password}")
    else:
        print("Invalid choice. Please choose a valid option.")

if __name__ == "__main__":
    password_generator()
