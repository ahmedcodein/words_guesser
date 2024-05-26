# Word Guesser

**"The difference between the almost right word and the right word is really a large matter.
It's the difference between the lightning bug and the lightning", - Mark Twain**

## 1. Introduction

The word guesser game is a game revolves around figuring out what word the computer is picked.
The player then try to guess the word letter by letter. The player wins if all the guessed letters
are correct given a limited number of tries/chances.
The number of chances is defined as how many wrong letters are entered by the player.
The player has three type of chances based on the difficulty choice. The difficulty choices are:

- Easy with three chances. There the picked word is a three-letter word
- Intermediate with five chances. There, the picked word is a five-letter word
- Difficult with six chances. There, the picked word is a six-letter word

## 2. Development Process

The process followed by the author consists of five phases, these are:

1. Research
2. Objective
3. Requirements Definition
4. Planning
5. Execution

These phases are presented below with a detailed account of each phase is presented in the subsequent sections.

### 2.1. Research and Selection Criteria

The research phase commences with a survey on Portfolio Project 3 (PP3) works published by Code Institute(CI) students on the pear-review channel.
There is a wealth of information there where the author is able to extract and learn from. Additionally, other searches are also
conducted on YouTube and relevant websites.
A summary of the reasons of choosing this game is:

1. Satisfactory amount of resources is available to extract information about the game. Whether under the word guesser name, or Hangman etc..., the game seems to be very popular among python developers. This makes it a good candidate since it is relatively easy to find information about how to approach the development. 
2. Although, it is limited in its scope, its code can cover multiple python concepts. Hence, it represents a low-risk sand-box to learn those concepts considering the available time for PP3.

### 2.2. Project Objective

From the author perspective, the main objective of developing this game is to learn Python. In particular, the author's intention from the beginning of the research phase is to implement the PP3 with Classes in mind as apposed to a function-based project. The main reason for that is that the use of classes is what distinguished an Object Oriented Programming (OOP) from other programming language that do not posses such capability. In PP2, the author exposed himself to the use of functions with JavaScript. Therefore, thinking in terms of functions is successfully comprehended. For that reason, building python project with functions will not help the author much in his learning endeavour in this training program. Therefore, in addition to learn programming with Python, the secondary goal is to learn how to program with classes.

#### 2.2.1. Game Owner Objectives

1. Easy to understand and simple to navigate
2. Engaging by having dynamic and colorful responses and presentation
3. Challenging through the introduction of multiple difficulty levels

#### 2.2.2. Game Visitor Objectives

1. Simple to understand and fun to play
2. Engaging and challenging

### 2.3. Game Requirements

Based on the main objectives presented in 2.2, 2.2.1 and 2.2.2, the following list of requirements is distilled:

1. The game is python classes-based code
2. A landing window welcoming the player
3. A simple, yet informative list of instructions to lead the player as how to play
4. A way to collect the player name
5. The game has three difficulty levels, easy, intermediate and difficult
6. A possibility to allow the player to choose the difficulty level
7. A game Dashboard displaying the game settings and status
8. A way to allow the player to restart or exit the game

### 2.4. Planning

#### 2.4.1. Game Logic

During the planning phase, the author chooses to write a pseudocode for this project. Although, this is not part of the assessment requirements of this project and it is a time consuming, the author takes the risk of writting it. The reason is that by writting the pseudocode, four paramount purposes are served, these are:

1. Helping the author to comprehend the general logic of the game.
2. Helping the author to build a mental structure of the entire game. This aids the author to write the code with modularity in mind (let this modularity be functions or classes) with each module as simple as possible.
3. Helping the author to correct any misperception about how the author thinks the program would behave and how it actually behaves when the code runs.
4. Helping the author to practice the art of creating pseudocodes as early as possible in his software development journey.

The following pseudocode represents the core of the game logic only. Form the author perspective, the core of the game logic is what matters for this project. Therefore, the final code, and only if the time allows, may include additional modules, e.g. for game decorations etc. 
Any additional code will have been written in the final stages of the implementation shall not be included in this pseudocode. Nevertheless, any change that has a direct impact on the core of the game logic is planned be updated here.

###### Word Guesser Pseudocode

```
words_storage:

    - create a words list
    - return word_storage

initiate_game:

    - display a welcome message
    - display the instructions
    - go to player_name

player_name:

    - input: Please input your first name:
        - if the input name is more than 20 or it is not part of the english alphabit:
            - display: Please provide a valid name with less than 21 letters
        - else: 
            - display: Hello “Player’s first name”
            - go to difficulty_selection

difficulty_selection:

    - input: Please choose the difficulty level, enter 1,2 or 3:
        1.	easy  		
        2.	intermediate 	
        3.	difficult

    - if the input is not 1,2 or 3:
        display: Please choose 1,2, or 3

    - return difficulty_level

word_selector:

    - if difficulty_level is easy:
        - randomly choose word with 3-letter length from the words_storage
    - else if difficulty_level is intermediate: 
        - randomly choose a word with 4-letter length from the words_storage
    - else:
        - randomly choose a word with no less than five-letter length from the words_storage
        - store the word in word_container
        - return word_container

num_of_chances_calculator:

    - num_of_chances = length of word_container
    - display num_of_chances: “You have got ‘num_of_chances ‘ chances”
    - return num_of_chances

player_guess:

    - input: Please Enter a letter:
    - if the letter is not part of the english alphabit:
        - display: Please enter a valid letter
        - return to Input
    - return the letter
    - go to letters_container

letters_container:

    - set count as the number of times this function is called
    - set guessed_letter_container to empty
    - if the count is not 0:
	    - if the letter in the letter_container
		    - display: “You chose this letter already, please select another one”
		    - Go to player_guess
	- else if:
        - add the guessed letter into the guessed_letter_container on the right index
        - display guessed_letter_container
        - return the letter
        - go to guess_evaluator

guess_evaluator:

    - if the letter in the word_container:
        - remove the letter from the word_container
        - display “letters_container, Great Job, you guessed the right letter!”
        - if word_container length is 0:
            - go to game_status
        - else:
            - go to player_guess
        - return word_container
    - else:
        - display: “Bad luck, you guessed the wrong letter”
        - decrease num_of_chances by 1
        - if num_of_chances is 0:
	        - go to game_status
        - else: 
            - go back to player_guess
            - return num_of_chances

game_status

    - if num_of_chances == 0:
	    - display: Bad luck, you lost this time
	    - go to restart_the_game	
    - if the length of the word_container == 0:
	    - display: Congratulations, you won!
	    - go to restart_the_game

Restart_game:

    - display: Do you want to restart the game?Yes/NO?
        - yes:
            - go to difficulty_selection
	    - no:
		    - exit the game

```

#### 2.4.2 The Conceptual Data Model

In this section, the conceptual data model of game is presented. Up until this point, only the initial parts of the game is considered when developing the data model.

![Conceptual Data Model](docs/images/conceptual_data_model.png)
### 2.5. Execution

#### 2.5.1. Technologies Used

The following list of technologies are used to develop the game:

1. Python: Programming Language
2. GitHub: Development Platform
3. Gitpod: Cloud Development Environment
4. Heroku: Development Platform
5. CI Python Linter: Python code style convention checker 

#### 2.5.2 Test Results

The test results are summarized in the table below.

| Test ID No. | Test Name | Test Result | Test Comment|
| ----------- |---------- |------------ |------------ |
| 1 | | | |

#### 2.5.3. Bugs

##### 2.5.3.1. Fixed Bugs

| Bug ID No. | Bug Position | Bug Description | Bug Solution | Comment|
| -----------| ----------- |---------- |------------ |------------ |
|1| | | | |

##### 2.5.3.2. Unfixed Bugs

## 2.5.4. Deployment, Clone and Fork Procedures

The following procedure is implemented to deploy the game on Heroku platform:

1. Create a list of requirements/dependencies for the game. In order to that, the following steps is to be executed:
    - Go to the command line terminal of development environment (Gitpod)
    - Type "pip3 freeze > requirements.txt" (requirements.txt is the file where the list of requirements is stored)
    - Add this change and commit it
    - Push the change to the GitHub repository
2. Sign in to Heroku account 
3. On Heroku dashboard, click on "Create a new app" button
4. Within the "Create New App" window, go to the "App name" input field and type in an App name
5. Within the same window, choose your region from the "Choose region" dropdown menu
6. Click on "Create app" button
7. New window opens for the App that is just created
8. Within this window, from the 7 taps available, select "Settings"
9. Within the setting tap window, go to "Confg Vars"
10. Click on "Create Confg Vars"
11. Two input fields appear, one for key and one for value
    - Within the "key" input field type: PORT
    - Within the "value" field type: 8000
    - Click on "Add"
12. Scroll down to "Buildpacks", within the Buildpacks, follow the listed sub-steps below:
    - Click on "Add buildpacks"
    - A "Add buildpack" window opens
    - From the list, choose "Python" first
    - Click on "Save changes" button
    - From the same list, choose "nodejs" second
    - Click on "Save changes" button
    - Ensure Keeping the order packs as described in last 4 sub-steps
13. Now go to the "Deploy" tap right at the top of the window
14. Within the "Deployment method" row, click on "GitHub" button
15. Within the "Connect to GitHub" (One row down the Deployment method) click on "Connect to GitHub"
16. Wait a bit for loading
17. Now on the same row and within the search field, type the name of the project repository and click on "Search" button
18. Now click connect
19. Once it is connected to the project repository, scroll down to "Manual Deploy"
20. Within this row, click on "Deploy Branch"
21. Once the deploy log is finished, a message appears and hopefully says: "You app was successfully deployed"
22. Below it a "View" button appears as well
22. Click on the "View" to open the deployed project on a new browser tap 

Note: Throughout the development, the author chooses only the manual deployment.


The following procedure is implemented to clone from the GiTHub repo into Gitpod:

1. Go to your repositories 
2. Click on the new created project repository
3. Go to the code in the upper right corner
4. Click on the Code dropdown menu
5. Select local 
6. Select Clone/HTTPs
7. Copy the url provided
8. Open new browser tap
9. Open your Gitpod Workspace
10. Create new workspace
11. Click on select new Repository
12. Paste the url in input window
13. Click continue

For any person interested to work on the source code of this project, here is the procedure that needs to be followed to make a fork.

1. Go to ahmedcodein repositories
2. Click on word_guesser repo
3. In the upper right corner, click of fork drop down menu
4. Click on create new fork
5. Create new fork window opens
6. Select the owner of the repo
7. Add a repo name
8. Add a description if needed
9. Click create fork 


## 3. Features

## 4 Future Work

## 5 Credits

### 5.1 References

### 5.2. Content and Tools

### 5.3. Acknowledgement

I would like to express my sincere gratitude to Mr. David Bowers for his outstanding mentorship. With every project, he proved 
again and again his dedication and integrity to provide all what a student needs to success. His encouragement to use classes for 
this project and the provision of further resources on the topic have helped me immensely in this project.
I would also like to thank my family for playing the game and providing their feedback on its outlook and interface.