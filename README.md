def encrypt_caesar_cipher(message, shift):
    encrypted_message = ''
    for char in message:
        if char.isalpha():
            shift_amount = shift % 26
            if char.islower():
                start = ord('a')
                offset = (ord(char) - start + shift_amount) % 26
                encrypted_char = chr(start + offset)
            elif char.isupper():
                start = ord('A')
                offset = (ord(char) - start + shift_amount) % 26
                encrypted_char = chr(start + offset)
            encrypted_message += encrypted_char
        else:
            encrypted_message += char
    return encrypted_message

def decrypt_caesar_cipher(encrypted_message, shift):
    decrypted_message = ''
    for char in encrypted_message:
        if char.isalpha():
            shift_amount = shift % 26
            if char.islower():
                start = ord('a')
                offset = (ord(char) - start - shift_amount) % 26
                decrypted_char = chr(start + offset)
            elif char.isupper():
                start = ord('A')
                offset = (ord(char) - start - shift_amount) % 26
                decrypted_char = chr(start + offset)
            decrypted_message += decrypted_char
        else:
            decrypted_message += char
    return decrypted_message

def main():
    print("Caesar Cipher Program")
    print("1. Encrypt")
    print("2. Decrypt")
    choice = input("Enter choice (1 or 2): ").strip()
    
    if choice not in ['1', '2']:
        print("Invalid choice. Exiting.")
        return
    
    message = input("Enter the message: ").strip()
    shift = int(input("Enter the shift value: ").strip())
    
    if choice == '1':
        result = encrypt_caesar_cipher(message, shift)
        print(f"Encrypted message: {result}")
    elif choice == '2':
        result = decrypt_caesar_cipher(message, shift)
        print(f"Decrypted message: {result}")

if __name__ == "__main__":
    main()
