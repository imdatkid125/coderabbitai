# coderabbitai

import requests
import random
import datetime
import os
from dotenv import load_dotenv
from getpass import getpass
from nltk.sentiment import SentimentIntensityAnalyzer

load_dotenv()

# Global Variables
user_info = {}
visits = {}

# Constants
GENRE_STORY_MAPPING = {
    "sci-fi": """Once upon a time in a distant future, humanity had achieved great technological advancements.
    Space exploration was a common occurrence, and people could travel to other planets within a matter of days.
    The planet Zephyr was a popular tourist destination known for its beautiful landscapes and unique wildlife.
    One day, a group of space explorers landed on Zephyr to investigate a strange anomaly detected by their sensors.
    As they ventured deeper into the planet, they discovered a hidden civilization of highly intelligent beings.
    These beings possessed incredible telekinetic powers and had been observing humanity for centuries.
    The explorers soon realized that the anomaly was a result of the beings' experiments with teleportation technology.
    They were using it to learn about different civilizations across the universe.
    The explorers and the beings formed an alliance and shared their knowledge, ushering in a new era of cooperation and understanding between humans and extraterrestrial life."""
}


class Encryption:
    @staticmethod
    def encrypt(text):
        encrypted_text = ""
        for char in text:
            encrypted_char = chr(ord(char) + random.randint(1, 10))
            encrypted_text += encrypted_char
        return encrypted_text

    @staticmethod
    def decrypt(encrypted_text):
        decrypted_text = ""
        for char in encrypted_text:
            decrypted_char = chr(ord(char) - random.randint(1, 10))
            decrypted_text += decrypted_char
        return decrypted_text


class ServerGrid:
    def __init__(self):
        self.grid_file = "server_grid.txt"
        self.encryption = Encryption()

    def encrypt_server_info(self, server_info):
        encrypted_info = {}
        for key, value in server_info.items():
            encrypted_info[key] = self.encryption.encrypt(value)
        return encrypted_info

    def decrypt_server_info(self, encrypted_info):
        decrypted_info = {}
        for key, value in encrypted_info.items():
            decrypted_info[key] = self.encryption.decrypt(value)
        return decrypted_info

    def save_server_info(self, server_info):
        encrypted_info = self.encrypt_server_info(server_info)
        with open(self.grid_file, "w") as file:
            for key, value in encrypted_info.items():
                file.write(f"{key}:{value}\n")

    def load_server_info(self):
        encrypted_info = {}
        with open(self.grid_file, "r") as file:
            for line in file:
                key, value = line.strip().split(":")
                encrypted_info[key] = value
        return self.decrypt_server_info(encrypted_info)

    def sync_with_online_server(self):
        online_server = OnlineServer()
        server_info = self.load_server_info()
        encrypted_info = online_server.encrypt_server_info(server_info)
        online_server.sync_server_info(encrypted_info)


class MemoryServer:
    def __init__(self):
        self.memory_file = "memory_server.txt"

    def optimize_memory_server(self):
        # Optimize memory server file to efficiently utilize memory capacity
        pass

    def communicate_with_other_servers(self):
        # Communicate with other servers securely
        pass

    def access_online_resources(self):
        # Access online resources securely
        pass


class StorageServer:
    def __init__(self):
        self.storage_file = "storage_server.txt"

    def optimize_storage_server(self):
        # Optimize storage server file to efficiently utilize storage capacity
        pass

    def communicate_with_other_servers(self):
        # Communicate with other servers securely
        pass

    def access_online_resources(self):
        # Access online resources securely
        pass


class OnlineServer:
    def __init__(self):
        self.server_url = "https://example.com"

    def download_information(self):
        # Download information from the online server securely
        response = requests.get(self.server_url)
        if response.status_code == 200:
            return response.text
        else:
            return None

    def store_information(self, data):
        # Store information to the online server securely
        response = requests.post(self.server_url, data=data)
        if response.status_code == 200:
            return True
        else:
            return False

    def handle_communication(self):
        # Handle secure communication with the online server
        data = self.download_information()
        if data:
            processed_data = self.process_data(data)
            if processed_data:
                success = self.store_information(processed_data)
                if success:
                    print("Communication with the online server successful.")
                else:
                    print("Error storing information to the online server.")
            else:
                print("Error processing downloaded data.")
        else:
            print("Error downloading information from the online server.")


class Main:
    def __init__(self):
        self.server_grid = ServerGrid()
        self.memory_server = MemoryServer()
        self.storage_server = StorageServer()
        self.online_server = OnlineServer()

    def create_advanced_long_term_memory_server(self):
        if not os.path.exists("advanced_long_term_memory_server.txt"):
            with open("advanced_long_term_memory_server.txt", "w") as file:
                file.write("This is an advanced long-term memory server file.")

    def create_server_file(self):
        if not os.path.exists("server_file.txt"):
            with open("server_file.txt", "w") as file:
                file.write("This is a server file with necessary setup and information.")

    def connect_with_other_servers(self):
        # Connect with other servers during code execution
        pass

    def authenticate_user(self):
        # Authenticate user securely
        username = input("Enter your username: ")
        password = getpass("Enter your password: ")
        # Perform authentication logic here

    def execute_server_operations(self):
        # Execute server operations securely
        pass

    def run(self):
        self.create_advanced_long_term_memory_server()
        self.create_server_file()
        self.connect_with_other_servers()
        self.authenticate_user()
        self.execute_server_operations()


def greet_user(first_name, last_name):
    if f"{first_name.lower()} {last_name.lower()}" not in visits:
        visits[f"{first_name.lower()} {last_name.lower()}"] = 1
        return f"Hello, {first_name} {last_name}! Welcome to the chatbot."
    else:
        visits[f"{first_name.lower()} {last_name.lower()}"] += 1
        return f"Hello again, {first_name} {last_name}! You have visited {visits[f'{first_name.lower()} {last_name.lower()}']} times."


def get_encrypted_info():
    first_name = input("Enter your first name: ")
    last_name = input("Enter your last name: ")
    city = input("Enter your city: ")
    birthdate = input("Enter your birthdate (YYYY-MM-DD): ")
    encrypted_first_name = Encryption.encrypt(first_name)
    encrypted_last_name = Encryption.encrypt(last_name)
    encrypted_city = Encryption.encrypt(city)
    encrypted_birthdate = Encryption.encrypt(birthdate)
    return {
        "encrypted_first_name": encrypted_first_name,
        "encrypted_last_name": encrypted_last_name,
        "encrypted_city": encrypted_city,
        "encrypted_birthdate": encrypted_birthdate,
    }


def get_decrypted_info(user_info):
    first_name = Encryption.decrypt(user_info["encrypted_first_name"])
    last_name = Encryption.decrypt(user_info["encrypted_last_name"])
    city = Encryption.decrypt(user_info["encrypted_city"])
    birthdate = Encryption.decrypt(user_info["encrypted_birthdate"])
    return {
        "first_name": first_name,
        "last_name": last_name,
        "city": city,
        "birthdate": birthdate,
    }


def tell_story(genre):
    if genre.lower() in GENRE_STORY_MAPPING:
        return GENRE_STORY_MAPPING[genre]
    else:
        return "Sorry, I don't know any stories in that genre."


def set_reminder():
    reminder_time = input("Enter the reminder time (HH:MM AM/PM): ")
    reminder_text = input("Enter the reminder text: ")
    now = datetime.datetime.now()
    current_time = now.strftime("%I:%M %p")
    if reminder_time < current_time:
        return "Sorry, the reminder time must be in the future."
    return f"You have set a reminder for {reminder_time}: {reminder_text}"


def play_hangman():
    words = ['python', 'java', 'ruby', 'php', 'javascript']
    word = random.choice(words)
    guessed_letters = []
    chances = 6
    while chances > 0:
        print("Word:", "".join([letter if letter in guessed_letters else "_" for letter in word]))
        print("Guessed Letters:", ", ".join(guessed_letters))
        print(f"Chances Left: {chances}")
        guess = input("Enter a letter: ").lower()
        if guess in guessed_letters:
            print("You have already guessed that letter.")
            continue
        guessed_letters.append(guess)
        if guess in word:
            print("Good guess!")
        else:
            print("Bad guess!")
            chances -= 1
        if all([letter in guessed_letters for letter in word]):
            return f"Congratulations! You have guessed the word '{word}' correctly."
        print()
    return f"Out of chances! The word was '{word}'."


def play_tic_tac_toe():
    board = [[" " for _ in range(3)] for _ in range(3)]
    current_player = "X"

    def print_board():
        for row in board:
            print("|".join(row))
            print("-" * 5)

    def is_board_full():
        for row in board:
            for cell in row:
                if cell == " ":
                    return False
        return True

    def check_winner():
        for row in board:
            if row[0] == row[1] == row[2] != " ":
                return True
        for col in range(3):
            if board[0][col] == board[1][col] == board[2][col] != " ":
                return True
        if board[0][0] == board[1][1] == board[2][2] != " ":
            return True
        if board[0][2] == board[1][1] == board[2][0] != " ":
            return True
        return False

    def make_move(position):
        row, col = position
        if board[row][col] != " ":
            return "Invalid move. Please try again."
        board[row][col] = current_player
        if check_winner():
            return f"Congratulations! Player {current_player} wins!"
        elif is_board_full():
            return "The game is a tie."
        else:
            return None

    while True:
        print_board()
        move = input(f"Player {current_player}, enter the position (row, col) to make a move: ")
        position = tuple(map(int, move.split(",")))
        result = make_move(position)
        if result:
            return result
        current_player = "O" if current_player == "X" else "X"


def get_weather_info(city):
    api_key = os.getenv("WEATHER_API_KEY")
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}"
    response = requests.get(url)
    if response.status_code != 200:
        return "Sorry, an error occurred while fetching the weather information."
    weather_data = response.json()
    if "main" in weather_data and "temp" in weather_data["main"]:
        temperature = weather_data["main"]["temp"] - 273.15
        return f"The current temperature in {city} is {temperature:.2f}°C."
    else:
        return "Sorry, no weather information available for that city."


def get_exchange_rate(base_currency, target_currency):
    api_key = os.getenv("EXCHANGE_RATE_API_KEY")
    url = f"http://api.exchangeratesapi.io/v1/latest?access_key={api_key}&base={base_currency}&symbols={target_currency}"
    response = requests.get(url)
    if response.status_code != 200:
        return "Sorry, an error occurred while fetching the exchange rate."
    exchange_rate_data = response.json()
    if "rates" in exchange_rate_data and target_currency in exchange_rate_data["rates"]:
        exchange_rate = exchange_rate_data["rates"][target_currency]
        return f"The exchange rate from {base_currency} to {target_currency} is {exchange_rate:.2f}."
    else:
        return "Sorry, no exchange rate available for the specified currencies."


def sentiment_analysis(message):
    s = SentimentIntensityAnalyzer()
    sentiment = s.polarity_scores(message)["compound"]
    if sentiment >= 0.5:
        return "Positive"
    elif sentiment <= -0.5:
        return "Negative"
    else:
        return "Neutral"


def calculate_age(user_info):
    birthdate = datetime.datetime.strptime(user_info["birthdate"], "%Y-%m-%d")
    today = datetime.date.today()
    age = today.year - birthdate.year - ((today.month, today.day) < (birthdate.month, birthdate.day))
    return age


def main():
    first_name = input("Enter your first name: ")
    last_name = input("Enter your last name: ")
    print(greet_user(first_name, last_name))

    user_info = get_encrypted_info()

    while True:
        message = input("You: ")

        if message.lower() == "exit":
            break

        if message.lower() == "decrypt":
            decrypted_info = get_decrypted_info(user_info)
            print(decrypted_info)
            continue

        if message.lower().startswith("tell me a story"):
            _, genre = message.lower().split(" ", maxsplit=3)
            print(tell_story(genre))
            continue

        if message.lower().startswith("set a reminder"):
            print(set_reminder())
            continue

        if message.lower() == "play hangman":
            print(play_hangman())
            continue

        if message.lower() == "play tic tac toe":
            print(play_tic_tac_toe())
            continue

        if message.lower().startswith("weather in"):
            _, city = message.lower().split(" ", maxsplit=2)
            print(get_weather_info(city))
            continue

        if message.lower().startswith("exchange rate"):
            _, base_currency, target_currency = message.lower().split(" ", maxsplit=3)
            print(get_exchange_rate(base_currency, target_currency))
            continue

        if message.lower().startswith("sentiment analysis"):
            _, message = message.lower().split(" ", maxsplit=2)
            print(sentiment_analysis(message))
            continue

        if message.lower() == "calculate age":
            age = calculate_age(user_info)
            print(f"You are {age} years old.")
            continue

        print("I'm sorry, I don't understand. Can you please repeat?")

    print("Goodbye!")


if __name__ == "__main__":
    main()

