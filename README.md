import re

class SimpleChatBot:
    def __init__(self):
        self.responses = {
            'hi': 'Hello!',
            'hello': 'Hi there!',
            'how are you': 'I am a chatbot, so I don\'t have feelings, but thanks for asking!',
            'bye': 'Goodbye! Have a great day!',
            'what is your name': 'I am a simple chatbot created by OpenAI.',
        }

    def get_response(self, user_input):
        # Normalize the user input
        user_input = user_input.lower()
        
        # Check for the keyword in the user input
        for key in self.responses:
            if re.search(r'\b' + re.escape(key) + r'\b', user_input):
                return self.responses[key]
        
        return "Sorry, I don't understand that."

    def start_chat(self):
        print("Hello! I am a chatbot. Type 'bye' to exit.")
        while True:
            user_input = input("You: ")
            if user_input.lower() == 'bye':
                print("Chatbot: Goodbye!")
                break
            response = self.get_response(user_input)
            print("Chatbot:", response)

# Create a chatbot instance and start the chat
chatbot = SimpleChatBot()
chatbot.start_chat()
