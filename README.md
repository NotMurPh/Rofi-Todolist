# Rofi-Todolist
Bring Todolist's to your Rofi 🫠

## Why another rofi todolist ❓

Well i was using this awsome todolist https://github.com/claudiodangelis/rofi-todo made by claudiodangelis ❤️ for months and i found my self tinkering with it alot and the reason being that i just wanted to add support for multiple todolists and change the specical character used for addition as it was hard to use but in my mind the code wasn't very readable, over engineered and not easy to work with so i decided to make my own instead 🙂 and i wanted to share this project so you dont have to go through the same thing 🙃

## Features 📝

- Support for multiple todolists
- Simple and readable code thus you can easly do : 

  - Change todolists location and extension's
  - Change the special character used for addition 
  - Change/Remove the icon before each task
  - Add new features

## Preview 🎥

![](https://github.com/NotMurPh/Rofi-Todolist/blob/main/preview.gif)

## Installation 📥

For the installation simply clone the project to your favorite location 

```bash
cd ~/.local/bin
git clone https://github.com/NotMurPh/Rofi-Todolist.git
```

## Arguments 🪧

This script takes in two arguments which the first one is the list name and the second one is the task

```bash
Usage : todolist list_name [special_character]task
```

__❗ Note that list_name only takes in your todolist name and not the list path if you want to change the list path reffer to [Customization](https://github.com/NotMurPh/Rofi-Todolist#customization-) section down below__ ( list path by default ~/.config/rofi/list_name.todo )

If there is a special_character before the task like so `.task` this script add's `task` to specified todolist otherwise it tries removing it,
for the customization of the special_character reffer to [Customization](https://github.com/NotMurPh/Rofi-Todolist#customization-) section down below

## Usage 🧑🏻‍💻

For the intended use case ( with rofi ) you have to run the script using somthing like the following command: 

```bash
rofi -modi "general-todo:todolist general,movie-todo:todolist movie" -show general-todo
```

Alright lets break this command down,
so basically we first define our modes for rofi using `-modi` argument and the following format ( Spaces are just for clarification dont use spaces in the actual command )

```bash
# To define a custom rofi mode you need a name and a script you can also give the script some arguments
rofi -modi "mode_name : mode_script script_arguments"

# So for example if we want a general todolist we do the folowing:
rofi -modi "general-todo : /path/to/todolist/script general"
# where general-todo is the rofi mode_name 
# and /path/to/todolist/script is the path of todolist script ( if correctly cloned ~/.local/bin/Rofi-Todolist/todolist )
# and general is the first argument of the script which is the todolist name

# If you want multiple todolists use , between rofi modes like so:
rofi -modi "mode_name : mode_script script_arguments , mode_name2 : mode_script2 script_arguments2"

# An example for that would be:
rofi -modi "general-todo : /path/to/todolist/script general , movie-todo : /path/to/todolist/script movie"
```

Then you have to tell rofi to show one of your modes using `-show` argument like so:

```bash
# -show Argument takes a mode_name so in our example it would be:
rofi -modi "general-todo : /path/to/todolist/script general , movie-todo : /path/to/todolist/script movie" -show general-todo
# or
rofi -modi "general-todo : /path/to/todolist/script general , movie-todo : /path/to/todolist/script movie" -show movie-todo
```

Once rofi is showen you can see your tasks 👀 and you can type to search through them 🔍 or you can type the special_character ( its . by default, for the customization of the special_character reffer to [Customization](https://github.com/NotMurPh/Rofi-Todolist#customization-) section down below ) followed by a task to add that to your todo list ➕ for example `.Do the dishes + Enter_key` and there you have it.

Finally if you have multiple todolists depending on your rofi theme supporting it you can click on other lists in rofi to switch between them, or by default you can just hit `Alt+Number_keys` like `Alt+1` and `Alt+2` to do the same thing.

## Customization 🔧

### Lists location and extension's 📍

To change lists location simply change the path between `list=` and `"$list_name".todo` in the line 7 of the file called todolist

```bash
# So for example change this:
list=~/.config/rofi/"$list_name".todo
# to:
list=/home/murphy/randomfolder/"$list_name".todo
```

And to change the lists file extension's simply change `.todo` in line 7 of the file called todolist to whatever you want

```bash
# So for example change this:
list=~/.config/rofi/"$list_name".todo
# to:
list=~/.config/rofi/"$list_name".txt
```

### Special_character 💬

To change the Special_character simply change the character between `""` in line 4 of the file called todolist

```bash
# So for example change this:
special_char="."
# to:
special_char="+"
```

### Task icon ☑️

To change/remove the icon before each task simply change ` ` in line 15 of the file called todolist

```bash
# So for example change this:
echo " $task" >> "$list"
# to:
echo "☑️ $task" >> "$list"
# or:
echo "$task" >> "$list"
```

## Thanks for visiting 🙃

Leave a like if you like 😉
