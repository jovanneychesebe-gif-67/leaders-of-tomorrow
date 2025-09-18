import time

def slow_print(text, delay=50):
    """Prints text slowly for dramatic effect."""
    for char in text:
        print(char, end='', flush=True)
        time.sleep(delay / 1000)  # delay is in milliseconds
    print("\n")

class TechJusticeGame:
    def __init__(self):
        # Story nodes with text and choices
        self.story = {
            0: {
                "text": "You are Jordan, the CEO of a leading tech company. Your team has developed a cutting-edge AI that could revolutionize healthcare. "
                        "However, it requires access to sensitive patient data. Should you proceed with the launch?",
                "choices": {
                    "1": {"text": "Proceed with the launch, arguing the technology could save lives.", "next": 1},
                    "2": {"text": "Delay the launch and investigate privacy concerns more thoroughly.", "next": 2}
                }
            },
            1: {
                "text": "The AI is launched and is assisting doctors successfully. However, a whistleblower claims the AI is biased against minority groups. How do you respond?",
                "choices": {
                    "1": {"text": "Ignore the whistleblower, insisting the AI’s benefits outweigh concerns.", "next": 3},
                    "2": {"text": "Launch a full investigation and pause the project until issues are resolved.", "next": 4}
                }
            },
            2: {
                "text": "You delayed the launch and found some serious privacy risks. Regulators have fined your company heavily. Shareholders demand quick settlement or you'll lose support. What do you do?",
                "choices": {
                    "1": {"text": "Pay the fine quickly to protect shareholders and company reputation.", "next": 5},
                    "2": {"text": "Fight the fine and push for stronger privacy laws, regardless of backlash.", "next": 6}
                }
            },
            3: {
                "text": "Ignoring the whistleblower leads to public outrage. The media calls you 'The Tech Tyrant.' Your board demands you step down. What is your response?",
                "choices": {
                    "1": {"text": "Step down gracefully and take responsibility.", "next": 7},
                    "2": {"text": "Fight to keep your position and double down on your decisions.", "next": 8}
                }
            },
            4: {
                "text": "Your investigation reveals bias in the AI. You redesign the system and regain public trust. Your leadership is praised for ethical responsibility.",
                "choices": {}
            },
            5: {
                "text": "Paying the fine protects your company short-term, but customers lose trust. Sales decline and competitors take over your market share.",
                "choices": {}
            },
            6: {
                "text": "Fighting the fine sparks controversy, but eventually new, stronger privacy laws are passed. Your company is seen as a leader in ethical tech.",
                "choices": {}
            },
            7: {
                "text": "You step down, and a new ethical leader takes over. Your company rebuilds trust and becomes a pioneer in responsible AI.",
                "choices": {}
            },
            8: {
                "text": "You refuse to step down, but your leadership causes further damage. The company is forced to shut down key projects and loses major clients.",
                "choices": {}
            }
        }
        self.current_node = 0

    def play(self):
        slow_print("Welcome to Tech Justice — A Game of Ethical Leadership.\n", 70)

        while True:
            node = self.story[self.current_node]
            slow_print(node["text"], 40)

            if not node["choices"]:
                # No choices means end of story
                slow_print("Thank you for playing Tech Justice! Reflect on your decisions and their consequences.", 70)
                break

            for key, choice in node["choices"].items():
                print(f"{key}. {choice['text']}")

            player_choice = input("\nChoose 1 or 2: ").strip()

            if player_choice in node["choices"]:
                self.current_node = node["choices"][player_choice]["next"]
            else:
                print("\nInvalid choice. Please enter 1 or 2.\n")

if __name__ == "__main__":
    game = TechJusticeGame()
    game.play()
