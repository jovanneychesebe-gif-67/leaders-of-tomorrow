import time

# Function to display text with a pause for dramatic effect
def slow_print(text, delay=1):
    for char in text:
        print(char, end='', flush=True)
        time.sleep(delay / 100)
    print()  # To move to the next line

# The story and decisions
class Game:
    def __init__(self):
        self.story = [
            {
                "text": "You are Jordan, the CEO of a leading tech company. Your team has developed a cutting-edge AI that could revolutionize healthcare. However, there is a dilemma. The AI requires access to sensitive patient data. Should you proceed with the launch?",
                "choices": [
                    {"text": "Proceed with the launch, arguing the technology could save lives.", "next": 1},
                    {"text": "Delay the launch and investigate privacy concerns more thoroughly.", "next": 2}
                ]
            },
            {
                "text": "The launch has begun, and the AI is being used to assist doctors in making better diagnoses. However, a whistleblower comes forward, claiming that the AI's algorithm is biased against minority groups. How do you respond?",
                "choices": [
                    {"text": "Ignore the whistleblower, claiming the system is too beneficial to be stopped.", "next": 3},
                    {"text": "Launch a full investigation and pause the project until you understand the issues.", "next": 4}
                ]
            },
            {
                "text": "Your company has been fined for violating data privacy laws. Shareholders are pressuring you to settle the case quickly. Do you care more about your company’s financial health or doing the right thing?",
                "choices": [
                    {"text": "Pay the fine quickly to avoid bad press and keep shareholders happy.", "next": 5},
                    {"text": "Challenge the fine and fight for stricter data privacy regulations.", "next": 6}
                ]
            },
            {
                "text": "As the company’s reputation continues to suffer, you face public backlash for ignoring ethical concerns. The media has dubbed you ‘The Tech Tyrant.’ The board is threatening to remove you. What will you do?",
                "choices": [
                    {"text": "Step down and accept responsibility for your actions.", "next": 7},
                    {"text": "Fight to keep your position and keep pushing the company’s agenda.", "next": 8}
                ]
            },
            # More steps can be added to the story...
        ]

        self.current_step = 0
        self.end_game = False

    def start_game(self):
        while not self.end_game:
            self.display_story()
            self.display_choices()

    def display_story(self):
        # Display the current story text
        slow_print(self.story[self.current_step]["text"], delay=50)

    def display_choices(self):
        # Get the choices for the current step
        choices = self.story[self.current_step]["choices"]
        
        # Display the choices
        for i, choice in enumerate(choices, 1):
            print(f"{i}. {choice['text']}")

        # Get the player's choice
        choice = input("\nWhat will you do? (1 or 2): ")

        # Validate the choice and move to the next step
        if choice == "1" or choice == "2":
            self.current_step = self.story[self.current_step]["choices"][int(choice) - 1]["next"]
        else:
            print("Invalid choice. Please select 1 or 2.")
            self.display_choices()

    def end_game(self):
        slow_print("The game has ended. Thank you for playing!", delay=100)
        self.end_game = True


# Initialize the game
game = Game()
game.start_game()
