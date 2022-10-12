# Download
The latest version (1.1.3.792) is [here](https://github.com/dlebansais/PgSurveyor-Disclosed/releases/download/v1.1.3.792/PgSurveyor.exe) with updated [release notes](https://github.com/dlebansais/PgSurveyor-Disclosed/blob/master/ReleaseNotes.md).

# PgSurveyor
This application helps players of Project: Gorgon (aka PG) to find gems and metal slabs while surveying in large, hostile zones. It does so by finding the shortest path to take, displaying visual clues such as the next place to go and the associated map to click. It can also calculate and display the location of motherlodes even though only their distance to the player is known.
All of this is 100% legit, the game client is untouched and no network packets are sniffed or injected.  

## How it works
The entire information that this program uses is extracted from game chat logs. Therefore, you will need to turn logs on in the game. Note: logging chat in files will likely be a VIP (i.e. paying) feature at some point when the game is released.

Visual clues are displayed over the game window in a separate, but transparent, window that sits on top of the game. This window is also transparent to clicks and therefore allows you to play the game with the visual clues displayed over it.
Because of the some restrictions in the operating system, this is possible only if the game is played in windowed mode. Full-screen mode is not supported.

# Instructions
I recommend to add the program to the Windows taskbar, this makes interacting with the game less weird.
Then, the program should be used as follow:

1. Launch the game and log in with your character. Move to the zone where you will survey, with your surveying maps.
2. Open the map window and resize it to make it relatively large, as PgSurveyor will display information over it.
3. Zoom (with the slider at the bottom of the map window) to make the entire zone visible.
4. Open the inventory, and resize it so that all survey maps are visible, aligned in rows starting at the first slot in the row. The program assumes a row is made of 10 maps, but this can be changed in the settings (see below). Also the game assumes all maps are visible and that no scrolling will be necessary to show them all.
5. Launch PgSurveyor. Two shiny, colored borders are displayed. The red border is for the map window, the purple border for the inventory window.
6. Drag the top-left and bottom-right corner of each border to align them with the corresponding window in the game. The border around the map window should adjust exactly around the zoomed map, and the border for the inventory window exactly around survey maps that will be clicked. The screenshot below demonstrates a game all set and ready to start.
7. Select the zone being surveyed, and the location from where you're starting (note: Kur Mountain will be added in a future release). Make sure your actual location in the game and the one selected in PgSurveyor match, otherwise the program will be completely lost and visual clues won't make any sense...

![Border around the map window](/Screenshots/MapBorder.png?raw=true "Border around the map window")

![Border around the inventory window](/Screenshots/InventoryBorder.png?raw=true "Border around the inventory window")

Next instructions depend on the type of survey: regular, or motherlodes.
  
## Regular (gems and mining) survey

8. Right-click each survey one at a time. You should see:
  + A little red dot added on the map, showing where the gem or metal is expected to be. This should match the game circle and if it doesn't it means the border around the map window isn't adjusted properly. You can still fix it at this stage.
  + A red, dotted border around the map you just clicked. The irregular border may look weird, but it gives you some space to click the next map. A future release may improve the look, but for now it shall do!
9. Keep clicking them to the last, then click the start button. This is the first button from the right, at the bottom of the border around the map window (check tooltips).
10. A yellow dot should appear on the map near the location of your character, and one of the survey maps in your inventory should be highlighted with a yellow border. Run to the yellow dot, right-click the highlighted survey map and blam! Collected!
11. A new yellow dot appears at the next location, and the corresponding map is highlighted again.
12. Rinse-repeat until all gems or metal slabs are collected.
 
Sometime the yellow dot is not the closest choice. Refrain from clicking that closest survey map first! It would completetly mess the rest of the run, and you'd have to start over and miss a bonus.

Instead, run to that far dot, and the next route should be good again. It is unfortunately unavoidable, and I worked quite a bit on a good algorithm, for a problem know to be hard to solve (technically, a NP-hard problem). PgSurveyor should be able to handle hundreds of maps, but it is currently impossible to do it perfectly, and too hard to do it better than players.

## Motherlode survey

Preliminary note: since only the distance to a motherlode is known, PgSurveyor uses triangulation to locate it. That means a map must be clicked 3 times from 3 different locations. After the first click we know that the motherlodes is on a circle, after the second click that it's at one of two possible spots (the intersection of two circles) and after the 3rd click we can pin-point the right spot. This is why in the following instructions you'll be told to move.

8. Right-click each survey one at a time. You should see:
  + A red circle centered around you, showing where the metal slab could be.
  + A red, dotted border around the map you just clicked. The irregular border may look weird, but it gives you some space to click the next map. A future release may improve the look, but for now it shall do!
9. Keep clicking all survey maps to the last.
10. Run to one of the other locations in the zone that are listed in the combo box of PgSurveyor, then select it. You can select it, then run, but be **extra careful** to return focus to the game before you start to run, otherwise hitting the arrow key will select yet another location, messing up the run and you'll have to start over.
11. At the second location, the last red circle has disappeared and the first map in the list is highlighted in blue. We are now at the two-dots stage. Right-click the highlighted survey map, this will show another circle centered around the new location, and one or two blue dots showing the possible locations of the motherlodes (sometimes the second blue dot is outside the map, but don't run to the first one yet!)
12. Keep clicking survey maps to the last.
13. Run to yet another location in the zone different than the other two, then select it in PgSurveyor.
14. The first survey map is highlighted in blue again, but this time when you click it it will show a red dot on the map. This is where triangulation has put the motherlode. Keep clicking all survey maps and see all red dots show up.
15. Click the start button. This is the first button from the right, at the bottom of the border around the map window (check tooltips).
16. A yellow dot should appear on the map near to the location of your character, and one of the survey maps in your inventory should be highlighted with a yellow border. Run to the yellow dot, right-click the highlighted survey map and blam! The motherlode appears!
17. Don't forget to collect the metal. The program updates only after collecting.
18. A new yellow dot appears at the next location, and the corresponding map is highlighted again.
19. Rinse-repeat until all metal slabs are collected.

## Other instructions

If you messed up at some point you can always just stop and click the Reset button to start over. You can also click the Exit button and then restart the program.

# Skip Map

In some situations it can be desirable to skip the current map. For example, if a motherlode is bugged and cannot be collected. In that case, clicking the **Skip Map** button will have the same effect as if the motherlode had been collected.

If the survey is a normal one (gem or metal), the map must be moved manually to the bottom of the inventory, because the application considers it's been consumed.
 
# Settings

You can change a few settings in the program. This is done by creating a text file called `settings.txt` in the same folder as PgSurveyor.exe. Each line in the file should be the name of the setting, followed by `:` followed by the value.

The following settings can be changed:

+ `InventoryRowLength`: the default is 10, but you can change it to the number of slots in each row of your inventory. 
+ `RightToLeft`: set to `yes` or `no` to change the map order in inventory. If set to `no` (the default), maps are expected to be clicked from left to right. Otherwise, from right to left.
+ `MapBorderThickness`: the default is 10, but you can change it to the thickness of the border of your choice around the map window. 
+ `MapPointThickness`: the default is 10, but you can change it to the size of points of your choice inside the map window. 
+ `InventoryBorderThickness`: the default is 10, but you can change it to the thickness of the border of your choice around the inventory window. 
+ `InventoryMapBorderThickness`: the default is 5, but you can change it to the thickness of the border of your choice around survey maps in the inventory window. 
+ `CanFlyOverWalls`: set to `yes` or `no` to take walls into account when calculating the shortest path. If set to `no` (the default), the algorithm will try to get around walls. This applies mostly to Serbule Keep.
+ `MapBorderBrush`, `MapThumbBrush`, `InventoryBorderBrush`, `InventoryThumbBrush`, `GripPressedBrush`, `GripReleasedBrush`: these are modifiable colors for the corresponding GUI elements. Note that *Grip* and *Thumb* are the same thing, this just a mistake in names that will be corrected in the next release (it will be *Grip*). You use colors like `Purple` or a custom color in ARGB format like `#FF0000FF` for blue.

A `settings.txt` file with default values would look like this:
    
    InventoryRowLength: 10
    RightToLeft: no
    MapBorderThickness: 10
    MapPointThickness: 10
    InventoryBorderThickness: 10
    InventoryMapBorderThickness: 5
    CanFlyOverWalls: no
    MapBorderBrush: Red
    MapThumbBrush: Green
    InventoryBorderBrush: Purple
    InventoryThumbBrush: Green
    GripPressedBrush: Orange
    GripReleasedBrush: Blue
    
## Disclaimer

This version of the program is far from perfect, and needs a better GUI or other improvements. Make sure to post your thoughts and suggestions on the game forum or send a private message to my account: Niph.
    
## Troubleshooting

If one of the corners of the map window or the inventory window has been moved outside the screen, you can either:
+ Move all other corners outside too, and then close the application in the taskbar. Upon restarting it, the problem will be detected and fixed automatically.
+ Use the `reset` command-line parameter to reset all borders.

## Linux
It's possible to run PGSurveyor under WINE in linux with some clever use of symlinks. By Default Project Gorgon will save your logs to `$HOME/.config/unity3d/Elder Game/Project Gorgon/ChatLogs/`
You'll need to have wine installed, and a prefix set up (wine will do this by default for you in most distributions)
By default your wine prefix will be `$HOME/.wine`

Provided the a default wine configuration...
```bash
export PROTON_ELDER_GAME=$HOME/.config/unity3d/Elder\ Game
export WINE_PREFIX=$HOME/.wine
ln -s $PROTON_ELDER_GAME $WINE_PREFIX/drive_c/users/$USER/AppData/LocalLow/Elder\ Game/Project\ Gorgon/
```
If you're using a custom wine configuration, you'll have to set the wine prefix to wherever you configured it to be.
Any questions you have about this should be directed to [Castone22](https://github.com/Castone22) instead of the program's author.

There exists a small bug with WINE and programs that create overlays where interacting with the overlay and clicking anything else will cause the wine virtual desktop to take focus, preventing you from interacting with anything on the screen (including the overlay).  You can work around this by switching windows (alt+tab in most distributions).  There's nothing the author can do to fix this, it is a bug in WINE itself.

# Certification

This program is digitally signed with a [CAcert](https://www.cacert.org/) certificate.
