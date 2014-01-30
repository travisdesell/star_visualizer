This is a simple star visualizer, which generates a 3D OpenGL representation of the stars.

It expects star files to be in LBR format, space separated, with the first line being the number of star points in the file.

It can be used as follows:

    ./star_visualizer <argument list>
    Possible arguments:
       --window_size <width> <height>  : width and height of the window <int> <int>
       --star_files <str>*             : files containing the stars (in LBR coordinates) followed by a cluster identifier (space separated)
       --modulo <int>                  : draw every <modulo> stars, default 1

For example:

    ./star_visualizer --window_size 1000 1000 --star_files ./stars_*.txt

This will display all the stars in the files in the current directory called "stars-<whatever>.txt".  Each star file's stars will be plotted with a different color.
