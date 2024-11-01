import nltk
import random
import string
import numpy as np

nltk.download('punkt')
nltk.download('wordnet')

# Sample responses
responses = {
    "greeting": ["Hello!", "Hi there!", "Greetings!", "How can I help you today?"],
    "goodbye": ["Goodbye!", "See you later!", "Take care!"],
    "thanks": ["You're welcome!", "Happy to help!", "Anytime!"],
    "default": ["I'm sorry, I didn't understand that.", "Can you rephrase?"]
}

# A simple function to generate a response
def respond(input_text):
    input_text = input_text.lower()
    tokens = nltk.word_tokenize(input_text)
    
    if "hello" in tokens or "hi" in tokens:
        return random.choice(responses["greeting"])
    elif "bye" in tokens:
        return random.choice(responses["goodbye"])
    elif "thank" in tokens:
        return random.choice(responses["thanks"])
    else:
        return random.choice(responses["default"])

# Main function to run the chatbot
def main():
    print("Chatbot: Hello! I'm a simple chatbot. Type 'exit' to end the conversation.")
    while True:
        user_input = input("You: ")
        if user_input.lower() == 'exit':
            print("Chatbot: Goodbye!")
            break
        response = respond(user_input)
        print("Chatbot:", response)

if __name__ == "__main__":
    main()
