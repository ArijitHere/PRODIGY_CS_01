# PRODIGY_CS_01
/* Create a Python program that can encrypt and decrypt text using the Caesar Cipher algorithm. Allow users to input a message and a shift value to perform encryption and decryption. */

import string

def encrypt(text, shift):
    """Encrypts the given text using Caesar Cipher with the specified shift."""
    result = []
    for char in text:
        if char.isalpha():
            alphabet = string.ascii_uppercase if char.isupper() else string.ascii_lowercase
            idx = alphabet.index(char)
            shifted_idx = (idx + shift) % 26
            result.append(alphabet[shifted_idx])
        else:
            result.append(char)
    return ''.join(result)


def decrypt(text, shift):
    """Decrypts the given text by reversing the Caesar Cipher shift."""
    return encrypt(text, -shift)


def main():
    print("Caesar Cipher Encryption and Decryption")
    choice = input("Do you want to (E)ncrypt or (D)ecrypt? ").strip().upper()
    if choice not in ('E', 'D'):
        print("Invalid choice. Please select 'E' or 'D'.")
        return

    message = input("Enter your message: ")
    try:
        shift = int(input("Enter shift value (integer): "))
    except ValueError:
        print("Invalid shift value. Please enter an integer.")
        return

    if choice == 'E':
        transformed = encrypt(message, shift)
        print(f"Encrypted message: {transformed}")
    else:
        transformed = decrypt(message, shift)
        print(f"Decrypted message: {transformed}")

if __name__ == "__main__":
    main()
