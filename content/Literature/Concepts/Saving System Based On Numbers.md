Imagine a player save loading / saving system that was based on numbers. Where each set of 10 numbers correspond to a particular piece of data for the game. Here is an example: 

```
Gold---------Age----------Wood---------Stone--------Sticks-------Meat-------
00000 00000  00000 00000  00000 00000  00000 00000  00000 00000  00000 00000

PlayerPosX---PlayerPosY---PlayerPosZ---PlayerName---Horses-------TownName---
00000 00000  00000 00000  00000 00000  00000 00000  00000 00000  00000 00000

TownPop------TimesDied----TimesSlept---TimesRunning-TimesAte-----TimesDrank-
00000 00000  00000 00000  00000 00000  00000 00000  00000 00000  00000 00000

TimePlayed---AnimalsFed---PeopleSaved--PeopleKilled-TotalDist----Sheep
00000 00000  00000 00000  00000 00000  00000 00000  00000 00000  00000 00000
```

each piece of data will need to be converted into a simple 10 digit number. 

Here are the data types:
```c++
int gold;
float age;
int wood;
int stone;
int sticks;
int meat;
int horses;
int sheep;

float playerPosX;
float playerPosY;
float playerPosZ;
string playerName;

int timesDied;
int timesSlept;
int timesSpentRunning; //corresponds to TimesRunning
int timesAte;
int timesDrank;
float timePlayed;
int animalsFed;
int peopleSaved;
int peopledKilled;
float totalDistanceTravelled; //corresponds to TotalDist

string townName;
int townPop;
```

## Saving
Should take all of the variables in order in a function that will convert each variable to a 10 digit number that corresponds to it (but will be stored as a string because we will have lots of numbers), and then appends the next number to the end of the previous number. 

For example, say we only have gold, age, and wood. 
First we would convert gold into a 10 digit counterpart, save it to a string.
next, we would convert the age into a 10 digit counterpart, and save it to a string and append that string to the previous one
lastly, we would convert the wood also, and again add it to the end of the first string. Then once all variables have been added to the string, we would save it as a .txt document 


## Auto Generate (NameOfGame)SaveGame
Given a list of strings in a txt file seperated by spaces and newlines, e.g.
```txt
GAMENAME Forest
int gold
int health
int age
int farms
float money
string playerName
```

we should go through each line, saving the first word up until a space as the variable type, and the next word until newline as the variable name. 

*Note that the first line will ALWAYS be a string == GAMENAME followed by a space, and then the name of the Game to be used for the .h and .cpp file generation*

### Generating the .h file
To begin, we need to generate the .h file for a new save game based on the extracted variables and game name from the txt file above. Each file will always have some of the same pieces, but some data will need to be procedurally created depending on which variables were found in the txt file above. For example,
```c++
#pragma once

#ifndef ANOTHER_WORLD_SAVE_GAME_H //replace ANOTHER_WORLD with FOREST as per game name
#define FOREST_SAVE_GAME_H //replace ANOTHER_WORLD with FOREST as per game name

#include "GameStateInterface.h"
#include <string>

class ForestSaveGame : public GameStateInterface { //replace AnotherWorld with Forest
public:
    int gold
	int health
	int age
	int farms
	float money
	string playerName
	//... include any other variables here that were found in the txt file

	//these two functions will always be the same
    std::string serialize() const override;
    void deserialize(const std::string& data) override;
};

#endif // FOREST_SAVE_GAME_H //replace ANOTHER_WORLD with FOREST as per the Game name
```
We would need to replace and add lines as indicated above and then save the resulting file to a string variable.
### Generating the .cpp file
Now that we have generated the .h file and saved it to a string, we can proceed with the generation of the .cpp to correspond to the (GameName)SaveGame.h file we have just created.
It needs at the top these includes:
```c++
#include "ForestSaveGame" //replace AnotherWorld with Forest as per game name
#include "GameStateController.h"
```
then we need to implement the two functions, serialize() and deserialize(). These functions simply follow exactly the data types we defined in the .h file and in the exact order as well. Here is an example of what those would look like. 
```c++
std::string ForestSaveGame::serialize() const { //replace AnotherWorld with Forest as per game name
    std::string saveString = "";

	//need to generate the following lines
    saveString += GameStateController::intTo10DigitString(gold);
    saveString += GameStateController::intTo10DigitString(health);
    saveString += GameStateController::intTo10DigitString(age);
    saveString += GameStateController::intTo10DigitString(farms);
    saveString += GameStateController::floatTo10DigitString(money);
    saveString += GameStateController::encodeString(playerName);
    //end generation lines

    return saveString;
}

void ForestSaveGame::deserialize(const std::string& data) { //replace AnotherWorld with Forest as per game name
    size_t pos = 0;

	//generate the following lines as per variables in .h file
    gold = GameStateController::tenDigitStringToInt(data.substr(pos, 10));
    pos += 10;
    health = GameStateController::tenDigitStringToInt(data.substr(pos, 10));
    pos += 10;
    age = GameStateController::tenDigitStringToInt(data.substr(pos, 10));
    pos += 10;
    farms = GameStateController::tenDigitStringToInt(data.substr(pos, 10));
    pos += 10;
    money = GameStateController::tenDigitStringToFloat(data.substr(pos, 10));
    pos += 10;
    playerName = GameStateController::decodeString(data.substr(pos, 10));
    pos += 10;
    //end generation of lines
}
```

As you can see, most of the file is unchanged, we just need to generate the slots as indicated above. 

### Summary
1. Read txt file
2. Get game name and variables
3. Generate .h file
4. Generate .cpp file
5. Save both file to disk with the game name prefixed like this GameNameSaveGame.cpp and GameNameSaveGame.h respectively.

#### Potential Solution (Python)
```python
def parse_txt_file(file_path):
    with open(file_path, 'r') as file:
        lines = file.readlines()

    game_name = lines[0].split()[1]
    variables = []

    for line in lines[1:]:
        type_name, var_name = line.strip().split()
        variables.append((type_name, var_name))

    return game_name, variables

def generate_h_file(game_name, variables):
    template = """
#pragma once

#ifndef {GAME_NAME}_SAVE_GAME_H
#define {GAME_NAME}_SAVE_GAME_H

#include "GameStateInterface.h"
#include <string>

class {GameName}SaveGame : public GameStateInterface {{
public:
{variable_declarations}

    std::string serialize() const override;
    void deserialize(const std::string& data) override;
}};

#endif // {GAME_NAME}_SAVE_GAME_H
    """

    variable_declarations = "\n".join([f"    {var_type} {var_name};" for var_type, var_name in variables])

    return template.format(GAME_NAME=game_name.upper(), GameName=game_name, variable_declarations=variable_declarations)

def generate_cpp_file(game_name, variables):
    template = """
#include "{GameName}SaveGame.h"
#include "GameStateController.h"

std::string {GameName}SaveGame::serialize() const {{
    std::string saveString = "";
{serialization_code}
    return saveString;
}}

void {GameName}SaveGame::deserialize(const std::string& data) {{
    size_t pos = 0;
{deserialization_code}
}}
    """

    serialization_code = []
    deserialization_code = []

    for var_type, var_name in variables:
        if var_type == "int":
            serialization_code.append(f"    saveString += GameStateController::intTo10DigitString({var_name});")
            deserialization_code.append(f"    {var_name} = GameStateController::tenDigitStringToInt(data.substr(pos, 10));")
        elif var_type == "float":
            serialization_code.append(f"    saveString += GameStateController::floatTo10DigitString({var_name});")
            deserialization_code.append(f"    {var_name} = GameStateController::tenDigitStringToFloat(data.substr(pos, 10));")
        elif var_type == "string":
            serialization_code.append(f"    saveString += GameStateController::encodeString({var_name});")
            deserialization_code.append(f"    {var_name} = GameStateController::decodeString(data.substr(pos, 10));")
        deserialization_code.append("    pos += 10;")

    return template.format(GameName=game_name, serialization_code="\n".join(serialization_code), deserialization_code="\n".join(deserialization_code))

def save_to_disk(game_name, h_content, cpp_content):
    with open(f"{game_name}SaveGame.h", 'w') as file:
        file.write(h_content)

    with open(f"{game_name}SaveGame.cpp", 'w') as file:
        file.write(cpp_content)

```
