import random
import string

# Lists of adjectives and nouns
adjectives = ["Cool", "Happy", "Brave", "Fast", "Clever", "Mighty", "Fierce", "Witty", "Jolly", "Lucky"]
nouns = ["Tiger", "Dragon", "Eagle", "Wolf", "Panther", "Shark", "Falcon", "Lion", "Cobra", "Phoenix"]

# Function to generate a random username
def generate_username(include_numbers=True, include_special_chars=True, length=10):
    adjective = random.choice(adjectives)
    noun = random.choice(nouns)
    username = adjective + noun
    
    if include_numbers:
        username += str(random.randint(10, 99))
    
    if include_special_chars:
        username += random.choice(string.punctuation)
    
    return username[:length]

# Function to save usernames to a file
def save_to_file(usernames, filename="usernames.txt"):
    with open(filename, "a") as file:
        for username in usernames:
            file.write(username + "\n")
    print(f"{len(usernames)} usernames saved to {filename}!")

# Interactive user input
def main():
    print("Welcome to the Random Username Generator!")
    num_usernames = int(input("How many usernames would you like to generate? "))
    include_numbers = input("Include numbers? (y/n): ").strip().lower() == "y"
    include_special_chars = input("Include special characters? (y/n): ").strip().lower() == "y"
    
    usernames = [generate_username(include_numbers, include_special_chars) for _ in range(num_usernames)]
    
    print("\nGenerated Usernames:")
    for username in usernames:
        print(username)
    
    save_option = input("Would you like to save these usernames to a file? (y/n): ").strip().lower()
    if save_option == "y":
        save_to_file(usernames)

if __name__ == "__main__":
    main()
