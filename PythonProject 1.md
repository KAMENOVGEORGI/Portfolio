
# 🌲 Shadowed Realms: A Text-Based Python Adventure 🌲

**Shadowed Realms** is a thrilling text-based adventure game where every decision matters. Traverse through mysterious lands, solve challenging riddles, and make daring choices to survive.

> My goal for this project is to develop fully this code and place it with a 5D VR gameplay. What you will see now is a small taste of how the game will look like and how the gameplay will be.
> Enjoy 🖤

---

## 🎮 Game Features
- **Dynamic Levels**: Explore 5 immersive levels, each with unique challenges and scenarios.
- **Riddle Challenges**: Test your intelligence against the Keeper of Riddles.
- **Checkpoint System**: Restart from your last stage after a defeat.
- **Multiple Endings**: Experience a different outcome with each playthrough.

---

## 📷 Level Previews

### 1. Forest of Shadows
![Forest Gameplay](Images/Forest.webp)
*Navigate an eerie forest where shadows seem alive.*

---

### 2. Cave of Echoes
![Cave Gameplay](Images/Caves.webp)
*Face the whispers of the past in a winding, dark cave.*

---

### 3. The Witch's House
![Witch House Gameplay](Images/Witch_House.webp)
*Explore an old house filled with strange potions and secrets.*

---

### 4. River of Reflection
![River Gameplay](Images/River.webp)
*Traverse a misty river that reveals hidden truths.*

---

### 5. Escape from the Forest
![Final Escape Gameplay](Images/final_escape.webp)
*Make your final stand in a bright forest clearing.*

---

## 🚀 Getting Started

### Prerequisites
- **Python 3.x** is required to run the game.
- Install required packages using:
  ```bash
  pip install -r requirements.txt

##Code <>

    import random

  # Introduction
    print("You are being chased by bandits and see a dense, dark forest in front of you.")
    command = input("What will you do?: ")


  # Function to validate choices with a three-strike penalty for invalid attempts
    def get_choice(options, strike_count):
    choice = input("Choose an option: ").strip().lower()
    while choice not in options:
        strike_count += 1
        if strike_count >= 3:
            print("You hesitated too long and lost your way. GAME OVER.")
            return "death", strike_count  # Indicate player must restart the game
        print("Try again.")
        print("A chill runs down your spine as if something is watching you closely...")
        choice = input("Choose an option: ").strip().lower()
    return choice, strike_count


  # The Keeper of Shadows NPC function to provide riddles
    def keeper_riddle():
    riddles = [
        ("I speak without a mouth and hear without ears. I have no body, but I come alive with wind. What am I?",
         "echo"),
        ("The more of this there is, the less you see. What is it?", "darkness"),
        (
        "I am taken from a mine, and shut up in a wooden case, from which I am never released, and yet I am used by almost every person. What am I?",
        "pencil lead"),
    ]
    riddle, answer = random.choice(riddles)
    print(f"The Keeper of Shadows whispers a riddle: '{riddle}'")
    response = input("What is your answer? ").strip().lower()
    if response == answer:
        print("The Keeper nods approvingly, granting you safe passage or a helpful item.")
        return True
    else:
        print("The Keeper chuckles softly, leaving you with an uneasy feeling.")
        return False


# Define each level as a function with stages and checkpoints
    def play_level(level, checkpoint=0):
    print(f"\n--- Level {level} ---")
    strike_count = 0  # Initialize strike count
    level_data = [
        {
            "name": "Forest of Shadows",
            "description": "A dark, eerie forest filled with twisting trees and shadows that seem to move.",
            "stages": [
                {
                    "stage_name": "The Keeper's Entrance",
                    "description": "You step onto a narrow path, and suddenly a cloaked figure appears. It's The Keeper of Shadows.",
                    "scenarios": [
                        {
                            "scenario": "The Keeper of Shadows blocks your path, their eyes gleaming with mystery.",
                            "options": [
                                "speak", "ignore", "ask for a riddle", "negotiate", "offer trade",
                                "hide", "use item", "observe quietly", "thank him", "refuse"
                            ],
                            "outcomes": {
                                "speak": "The Keeper speaks cryptically about hidden dangers in the forest.",
                                "ignore": "The Keeper watches you leave, and you feel a strange chill.",
                                "ask for a riddle": keeper_riddle(),
                                "negotiate": "The Keeper listens, then mutters a riddle for you to solve.",
                                "offer trade": "The Keeper accepts and provides a small charm.",
                                "hide": "The Keeper fades, whispering riddles that echo through the trees.",
                                "use item": "You show the Keeper an item, and he nods approvingly.",
                                "observe quietly": "You notice symbols etched into his cloak, adding mystery.",
                                "thank him": "The Keeper inclines his head slightly, almost amused.",
                                "refuse": "The Keeper vanishes, leaving you to find your own way."
                            },
                            "death_options": ["ignore", "refuse"],  # Certain death if disrespectful
                        },
                        {
                            "scenario": "A shadowy path lies ahead, with faint whispers calling you forward.",
                            "options": [
                                "approach", "ignore", "hide", "investigate", "run away",
                                "call out", "follow quietly", "observe from a distance", "move towards slowly",
                                "stay silent"
                            ],
                            "outcomes": {
                                "approach": "You step forward, and the whispers grow louder.",
                                "ignore": "You ignore the whispers but feel watched.",
                                "hide": "You stay hidden, waiting for the whispers to fade.",
                                "investigate": "You find a strange inscription on a tree, glowing faintly.",
                                "run away": "The whispers seem to follow you, growing louder.",
                                "call out": "A voice answers, leading you deeper into the shadows.",
                                "follow quietly": "You move quietly, and the whispers guide you to a clearing.",
                                "observe from a distance": "You watch the shadows, noticing strange movements.",
                                "move towards slowly": "You approach cautiously, and the path clears.",
                                "stay silent": "The whispers fade, leaving you with a sense of dread."
                            },
                            "death_options": ["run away", "call out"]  # Certain death for reckless choices
                        },
                    ]
                },
                {
                    "stage_name": "The Clearing",
                    "description": "The trees open up into a dark clearing surrounded by twisted branches.",
                    "scenarios": [
                        {
                            "scenario": "An eerie silence fills the clearing, and you see symbols etched into stones.",
                            "options": [
                                "inspect", "touch", "ignore", "pray", "study it closely",
                                "trace the symbols", "circle around", "move closer carefully", "look for clues", "wait"
                            ],
                            "outcomes": {
                                "inspect": "You feel an ancient energy emanating from the stones.",
                                "touch": "A sharp shock jolts you, leaving your hand numb.",
                                "ignore": "You leave the stones, but feel something is following you.",
                                "pray": "A faint light glows from the symbols, illuminating a path.",
                                "study it closely": "You notice markings that point to a hidden trail.",
                                "trace the symbols": "A strange warmth fills you, providing comfort.",
                                "circle around": "You find an old inscription on the back of a stone.",
                                "move closer carefully": "The symbols flicker as you approach.",
                                "look for clues": "You find markings that seem to tell a story.",
                                "wait": "The silence deepens, and shadows seem to close in."
                            },
                            "death_options": ["touch", "wait"],  # Reckless choices lead to fatal consequences
                        },
                        {
                            "scenario": "The Keeper reappears, blocking your way with a riddle.",
                            "options": [
                                "speak", "ignore", "ask for a riddle", "negotiate", "thank him",
                                "offer trade", "stay silent", "observe", "ask for guidance", "give him food"
                            ],
                            "outcomes": {
                                "speak": "The Keeper mutters a warning, then poses a riddle.",
                                "ignore": "The Keeper frowns, his eyes turning cold.",
                                "ask for a riddle": keeper_riddle(),
                                "negotiate": "The Keeper listens and offers you a cryptic hint.",
                                "thank him": "The Keeper inclines his head, giving you passage.",
                                "offer trade": "The Keeper accepts your offering and grants you an amulet.",
                                "stay silent": "The Keeper waits, then offers a riddle.",
                                "observe": "You notice strange symbols on his cloak.",
                                "ask for guidance": "The Keeper whispers a warning, then fades.",
                                "give him food": "The Keeper smiles, blessing your path forward."
                            },
                            "death_options": ["ignore", "stay silent"],  # Disrespect results in game over
                        },
                    ]
                },
            ]
        },
    ]

  # Process stages with checkpoints
    stages = level_data[level - 1]["stages"]

    for i in range(checkpoint, len(stages)):
        stage = stages[i]
        print(f"\n{level_data[level - 1]['name']} - {stage['stage_name']}")
        print(stage["description"])

        print(f"Checkpoint saved at {stage['stage_name']}")

        for scenario_data in stage["scenarios"]:
            print(f"\nScenario: {scenario_data['scenario']}")
            print("What will you do?")

   # Present choices and check for outcome with penalty for invalid attempts
            choice, strike_count = get_choice(scenario_data["options"], strike_count)
            if choice == "death":
                return False, i  # Player loses due to invalid choices

            if choice in scenario_data.get("death_options", []):
                print("You made a fatal mistake. GAME OVER.")
                return False, i  # Death; restart from checkpoint

            outcome = scenario_data["outcomes"][choice]
            print(outcome if not callable(outcome) else outcome)  # NPC riddle function if called

            # Level win check
            if i == len(stages) - 1 and random.random() <= 0.05:
                print("You have conquered this level and move to the next!")
                return True, i  # Win level and return checkpoint

        print(f"Checkpoint: Returning to {stage['stage_name']} if you fail.")

    print("End of level without success; you must replay some stages.")
    return False, i  # Lose level but return checkpoint


# Main game function
    def play_game():
    levels = 5
    level_checkpoints = [0] * levels

    for level in range(1, levels + 1):
        print(f"\nStarting Level {level}...")
        won_level = False

        while not won_level:
            won_level, checkpoint = play_level(level, level_checkpoints[level - 1])
            if not won_level:
                print(f"Restarting Level {level} from checkpoint: Stage {checkpoint + 1}.")
                level_checkpoints[level - 1] = checkpoint

        print(f"Level {level} complete!")

    # Final game win condition
    if random.random() <= 0.05:
        print("Legendary Status Achieved!")
        print("Ending: Your journey becomes a tale of bravery and resilience, remembered for ages.")
    else:
        print("Ending: Your journey remains incomplete, shrouded in mystery.")


# Start the game
    play_game()


📖 How to Play
Choose your actions carefully during each scenario.
Solve riddles to unlock rewards and safe paths.
Survive through all five levels to escape the forest. 

🛠 Technologies Used
Python 3.x
Random module for dynamic gameplay
Modular level and stage design for extensibility

📜 License
This project is licensed under the MIT License.

GitHub:KAMENOVGEORGI
Email:g.kamenovkanchev@gmail.com
