<a id="readme-top"></a>

<!-- PROJECT LOGO -->
<br />
<div align="center">
<h3 align="center">Path Finder Simulation</h3>
  <p align="center">
    You have just broken out of the detention level of a large and strangely moon-like space station. You need to find your way back to your old spacecraft of questionable space-worthiness to escape. Your adorable robot friend has hacked into the elevator system of the space station to assist you in your escape.
  </p>
  <p align="center">
    EECS 281 - January 2023
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li><a href="#features">Features</a></li>
    <li><a href="#requirements">Requirements</a></li>
    <li><a href="#description">Description</a></li>
    <li>
      <a href="#file-formats">File Formats</a>
      <ul>
        <li><a href="#map">Map</a></li>
      </ul>
      <ul>
        <li><a href="#coordinate-list">Coordinate List</a></li>
      </ul>
    </li>
    <li><a href="#routing-schemes">Routing Schemes</a></li>
    <li><a href="#command-line-arguments">Command-Line Arguments</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project
<p align="center">
  A program that identifies the shortest path between a given start and end point in a 3D maze, providing the user with the output necessary to find the directions using a map and/or coordinate system</p>
  
<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With
[![C++][cplusplus]][cplusplus-url]
[![Xcode][xcode]][xcode-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- FEATURES -->
## Features

<!--Use this space to show useful examples of how a project can be used.
Additional screenshots, code examples and demos work well in this space. You may also link to more resources.-->
- [ ] 3D Maze: read, store, access, and write
- [ ] Breadth first search (BFS w/ queue)
- [ ] Depth first search (DFS w/ stack)
- [ ] Allows for map and coordinate list as input and output
- [ ] Uses getopt_long() to handle command line arguments
- [ ] Utilized abstract data types (queue, stack, deque, etc.)
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- REQUIREMENTS-->
## Requirements
The program must run to completion within 35 seconds of total CPU time (user time) and must be able to process very large space stations (ie. up to several million locations)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Description
A space station is composed of up to 10 square levels with elevators to travel between levels. The description of a space station will be provided by an input file using a 3-D coordinate system and special characters.

The special characters and what they represent:
- [ ] ’.’ floor space
- [ ] ’#’ walls (the only character that cannot be walked on/through)
- [ ] ‘S’ your starting location at the detention level
- [ ] ‘H’ the hangar of the spacecraft location (the goal)
- [ ] ‘E’ corresponds to elevators that transport you from that location to the same row and column of the levels that have an elevator on the same location

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- FILE FORMATS -->
## File Formats

The input file is a simple text file specifying the layout of the space station and that is compatible with two input modes: Map Mode (M) and coordinate list mode (L)

<strong> Coordinate list mode exists so that we can express very large graphs with relatively few lines of a file, map input mode exists to express dense graphs (ones for which most of the tiles are not just floor space) in the smallest number of lines. </strong>

### Map

#### Input Mode
- [ ] For this input mode, the file header will start with an ‘M’ and contain a 2D map of characters defining each level
- [ ] Each input file starts with level 0 and ends with defined 'level'
<p>Example Input: </p>
<img width="462" alt="Screenshot 2024-09-14 at 17 30 31" src="https://github.com/user-attachments/assets/23a5aeb2-833a-4fa6-8501-33f589a28539">
<br/><br/>

#### Output Mode
- [ ] For this output mode, the map of the levels is printed, replacing existing characters in order to show the path that was taken
- [ ] Beginning at the starting location, each character representing the path is overwritten with either an ‘n’, ‘e’, ‘s’, ‘w’, or ‘0-9’ to indicate which tile you moved to next
<p>Example Output: </p>
<img width="348" alt="Screenshot 2024-09-14 at 17 35 48" src="https://github.com/user-attachments/assets/942463f2-c5a9-4bcb-b9d5-461ee1787906">
<br/><br/>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Coordinate List

#### Input Mode
- [ ] For this input mode, the file header will start with an ‘L’ and contain a list of coordinates for at least all non-floor space characters
- [ ] A coordinate is specified in precisely the following form: (level,row,column,character)
- [ ] The level values will be in the range, and the row and column values will be in the range
<p>Example Input: </p>
<img width="444" alt="Screenshot 2024-09-14 at 17 31 26" src="https://github.com/user-attachments/assets/144b55e7-683b-4450-a1a6-1fb2236cbcff">
<br/><br/>

#### Output Mode
- [ ] For this output mode, only the coordinates that make up the path you traveled are printed, including each step of the path from the start to the hangar
- [ ] The character of the coordinate should be ‘n’, ‘e’, ‘s’, ‘w’, or ‘0-9’ to indicate spatially which tile is moved to next
<p>Example Output: </p>
<img width="177" alt="Screenshot 2024-09-14 at 17 36 15" src="https://github.com/user-attachments/assets/143ff2ca-6c26-4c80-8049-6007526416c0">

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Routing Schemes

Two routing schemes were developed in order to get from the starting location to the hangar location tile:
- Depth-First Search: A routing scheme that uses a <strong>queue</strong> as the search container
- Breadth-First Search: A routing scheme that uses a <strong>stack</strong> as the search container

<strong>If a path exists, both will always lead you to the hangar</strong>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- COMMAND-LINE ARGUMENTS -->
## Command-Line Arguments (& Options)

--stack, -s
- [ ] The search container will be used like a stack and the routing scheme will perform a depth first search (DFS)
- [ ] The stack option may be invoked by calling the program with either --stack or -s, it accepts no arguments

--queue, -q
- [ ] The search container will be used like a queue and the routing scheme will perform a breadth first search (BFS)
- [ ] The queue option may be invoked by calling the program with either --queue or -q, it accepts no arguments

--output (M|L), -o (M|L)
- [ ] Indicates the output file format by the required argument, M (map format) or L (coordinate list format)
- [ ] If this option is not provided when running the program, the default output format is map format
- [ ] If specified, this option requires that an argument be provided, and the autograder will only use valid arguments

--help, -h
- [ ] This causes the program to print a helpful message about how to use the program and then immediately exit(0)
      
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
<!-- ## Contact

Allen Pinjic - apinjic@umich.edu -->

<!-- ACKNOWLEDGMENTS -->
 ## Acknowledgments

[EECS 281 Project Description](https://eecs281staff.github.io/p1-back-to-the-ship/#command-line-options)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[cplusplus]: https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white
[cplusplus-url]: https://cplusplus.com/
[xcode]: https://img.shields.io/badge/Xcode-007ACC?style=for-the-badge&logo=Xcode&logoColor=white
[xcode-url]: https://developer.apple.com/xcode/
