# Bash JSON Menu - **Build Just Menu**

*A Bash JSON Menu solution*

This allows the user to create a menu system that is driven completely by a single JSON file, as documented below.

## Use

- Place the bjm file in your run path... somewhere!

    Make certain to set the file to be executable.
  
  ```sudo chmod bjm 7555 ```

  This should dod the trick for you.

- Define your JSON file. 

    By default, the script will automatically load a file called menu.json from the same path as the menu script.

- Execute the menu by running bjm

    If your menu has a different named file, you may pass it in as a parameter 

    *eg.* bjm ./mymenu.json

## Features

This should be able to control ALL features just by edititing the JSON file. It is possible to control:

- Colors.
- Position on screen.
- All Text and Descriptions for both Menus and Menu Items.
- Multiple nested menus.

To naviaget through the menu, you can either use the menu item number to select, OR navigate by using the arrow keys.

## JSON File Specification Documentation

This specification outlines the structure and elements of the JSON configuration file used for defining a menu-based command-line interface.

### Elements
- **StartMenu:** String

    The entry point of the menu system.

    *Example:* "Main Menu"

- **MenuRow:** Integer (*Default 3*)

    The starting row for the menu. Where the NAME of the menu will start displaying from. Used with MenuCol.

    Example: 2

- **MenuCol:** Integer (*Default 10*)

    The starting column for the menu. Used in conjunction with MenuRow, and controls where the Menu Name is printed.

    Example: 8

- **MenuItemsRowOffset :** Integer (*Default 2*)

    Defines how many rows below the menu name that the menu items will start from.

    Example: 3

- **ItemDescCol:** Integer  (*Default 40*)

    The column where item descriptions are printed in.

    Example: 45

- **ItemDescWidth:** Integer (*Default 25*)

    How many columns of text are allowed for an item description before he description text i wrapped.

    Example: 30

- **MenuTitleColor:**    (*Default green*)

    Color of Menu Title text

- **MenuDescColor:**     (*Default magenta*)

    Color of the Menu Description text

- **MenuIndexColor:**    (*Default yellow*)

    Color of the Menu Item Index number 

- **MenuItemColor:**    (*Default cyan*)

    Color of the Menu Item name

- **MenuSelIndexColor:** (*Default green*)

    Color of the Currenlty selected Menu Item 

- **MenuSelDescColor:**  (*Default yellow*)
    
    Color of the Currenlty selected Menu Item Description

    Colors for various menu elements, using color names.

    - Possible values: 
        - "black"
        - "red"
        - "green"
        - "yellow"
        - "blue"
        - "magenta"
        - "cyan"
        - "white"
        - "bright_black"
        - "bright_red"
        - "lime"
        - "bright_yellow"
        - "bright_blue"
        - "bright_magenta"
        - "bright_cyan"
        - "bright_white"

- **CommandsToExec:** List of Strings

    Commands that can be executed within the menu. Ordinarily BASH scripts will execute just fine.

    Examples: "vim", "less", "more"

- **Menus**

    This is a List of Menu objects

    - **Menu Object:**
        
        Contains the following elements:

        - **Name:** String

            The name of the menu.

            Example: "Main Menu"

        - **Description:** String

            A brief description of the menu.

            Example: "This is the MAIN Menu"

        - **Items:** List of Item objects

            Item Object: Contains the following elements:

            - **Name:** String

                The name of the item.

                Example: "List"

            - **Command:** String     

                The command to be executed.

                Example: "ls -lah"

            - **Description:** String

                A brief description of the item.

                Example: "Runs a list command using the -lah parameters"

            - **Menu:** String (optional)

                The name of the menu to navigate to.

                Example: "Sub Menu"
