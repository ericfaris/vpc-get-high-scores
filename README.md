# high-score-get

This tool will pull high scores for tables that are setup in the Pinup Popper DB.

**Instructions**:

1. Confirm correct table name and author within Pinup Popper for every table you want to show high scores.

**Setup the batch file to run on Windows startup**

2. Copy the latest version of vpc-get-high-scores-image into the `c:\pinball\PinupPopper\LAUNCH` folder.

3. Create a .bat file called `GetAllHighScores.bat` in the `c:\pinball\PinupPopper\LAUNCH` folder.

4. Edit the `GetAllHighScores.bat` to look like the following:
    - vpc-get-high-scores-image.exe "YOUR PINUP SYSTEM FOLDER" "YOUR OTHER2 MEDIA FOLDER" "10" <--- this is max rows for high scores

5. Create a shortcut to `GetAllHighScores.bat`

6. Copy the shortcut to your Windows startup folder

**Setup scripts to run the vpc-get-high-scores-image.exe**

7. Pinup Popper Setup > Popper Setup Tab > Emulators > Visual Pinball X > Launch Setup Tab
    - Paste the following at the end of the Launch and Close Scripts:
        - `"[STARTDIR]LAUNCH\vpc-get-high-scores-image.exe" "[GAMENAME]" "[?Author?]" "[MEDIADIR]Other2" 10`
        
8. Save and Close

**Enable Display to Show Other2**

9. Pinup Popper Setup > Popper Setup Tab > GlobalConfig button > Displays tab
    - Set `Other 2` = `Active and Hidden`
    
10. Save

11. Pinup Popper Setup > Popper Setup Tab > Screens / Themes button

12. In Pup Pack Editor
    - Change Mode field of `Other` to `ForcePop`
    
13. Click "Save PuP-Pack" button

**Configure and Place the Other Display**

14. On the same "PuP Editor" screen, click "Configure Display/Locations" button

15. On the "PinUP Player DIsplays" window, click on `Other2` in the "Select Screen" list

16. Adjust this display to your liking.  This will be the display for the high scores.
    - Suggestions:
        - Rotation: `270`
        - Width: `2000`
        - Height: `1800`
        - Default State: `off`
        
17. Click "Save Settings" button

18. Close "PuP Pack Editor" window

**Configure key in PinUP Popper to display Other2 (the high score image)**

19. On "PinUP Popper Setup" window, click "Controller Setup" button

20. Assign key press to `Show Other` entry

21. Click "Close" button

22. On "PinUP Popper Setup" window, click "Exit Setup" button

**Add menu option to PinUP Popper Operator menu to update all high scores on demand**

23. In File Explorer, navigate to `{YOUR ROOT FOLDER}\PinUPSystem` folder

24. Click on `PopperOperatorEdit.exe`

25. In the "CSVBrowserForm" window, right click on the "Show Other" row.

26. Click Insert Row

27. Within the new row, enter as follows (fields not mentioned should be empty):
    - parentMenu: home
    - display: Update High Scores
    - function: launch
    - extra1: GetAllHighScores.bat
    - ingame: 2
    
28. Click Save

29. Close "CVSBrowserForm" window
