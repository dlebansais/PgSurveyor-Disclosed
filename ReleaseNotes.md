# 1.0.0.535

This release includes improvements to the shortest path algorithm. Consequently, it's become slightly slower.

# 1.0.0.528

Bug fix in the new algorithm.

# 1.0.0.527

This version introduces yet a new version of the shortest path algorithm. Hopefully, better overall for surveying.

Also:
+ Some bug fixes (but ore bugs may have been added)
+ Added support for checking for updates.
+ The GUI has been much improved internally, and looks slightly different now.
+ New locations added in Gazluk
+ The game should no longer freeze when searching for the shortest path.
+ Support for Treasure Cartography maps (and collecting them).

Note: Ilmari is still bad as a map.

# 1.0.0.119

This version includes more settings to customize the borders and points thickness.

# 1.0.0.112

This version brings 3 changes:
+ Added the boatman to the Serbule list.
+ Added a check to detect if an overlap (either the map of the inventory window) was moved outside the screen.
+ Added a setting: `RightToLeft`. Set it to `yes` to change the map click order in inventory.

# 1.0.0.104

This release adds a new feature. The skip map button let you skip a map, for instance when a motherlode is bugged, or the destination is unreachable.

Don't forget to move the skipped map to the bottom of inventory!

# 1.0.0.94

In this release:
+ Added Makara in Ilmari.
+ Improved the shortest path algorithm
+ Removed **Capture Map**, as it was not really useful.
+ Added the **Best Path** option. Warning: it makes calculating the path much slower.
+ Fixed a problem when mining a normal node while doing a run of motherlode nodes.
+ If you click the same map twice, it should count for only one map.

# 1.0.0.43

Adding motherlode surveys had broken normal mining surveys. Fixed.

# 1.0.0.42

Most bugs should be fixed now.

# 1.0.0.36
 
This release fixes 3 bugs:
+ Crash if surveying more than 50 maps (approximately)
+ Crash if collecting while clicking a map before starting the survey.
+ Maps can be outside the zone border and no longer appear at the opposite side.

A new bug has been introduced:
+ Sometimes the shortest path algorithm may forget a map, and will crash when the last map is collected.

# 1.0.0.28

+ Special locations in various zones have been checked and fixed. Also, the dependency on QuickGraph has been removed.
