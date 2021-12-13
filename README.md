<div id="top"></div>




<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]





<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/fedehub/fmcFlexibleAutomation">
    <img src="images/logo-black.png" alt="Logo" width="200" height="100">
  </a>

  <h3 align="center">Flexible automation course</h3>

  <p align="center">
    Final simmulation assignment for the Flexible Automation course 
    <br />
    <a href="https://github.com/fedehub/fmcFlexibleAutomation"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/fedehub/fmcFlexibleAutomation">View Demo</a>
    ·
    <a href="https://github.com/fedehub/fmcFlexibleAutomation/issues">Report Bug</a>
    ·
    <a href="https://github.com/fedehub/fmcFlexibleAutomation/issues">Request Feature</a>
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
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project
Design of a flexible manufacturing cell (FMC) with robot centred layout

### Project statement 

A car engine parts manufacturer approaches you seeking a robotic *automated solution* for one of their problem in their **loading** and **unloading** station. The station receives **three** **parts** of the engine. The job of the station is to:

*  segregate the products
*  load it to the **appropriate** loading line. 

Our task was to design a flexible manufacturing cell (FMC) with robot centered layout for the above function. 
The design should handle the requirements below:

- [x] Plant layout simulation
- [x] Robot simulation
- [ ] Analysis and optimization of the cell
- [ ] Report delivery

Please refer to #roadmap 



<p align="right">(<a href="#top">back to top</a>)</p>



### Built With

For realising this project, **Coppeliasim** robot simulator has been employed. This latter, due to its features, is considered as a very versatile solution for multi-robot applications. Controllers have been written in Lua.

* [Lua](https://www.lua.org/)
* [Coppeliasim](https://www.coppeliarobotics.com/)


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

Here are present some brief instructions for setting up my project locally, on your pc.


### Prerequisites

There are **no** specific requirements, other than:
* a good graphic card
* an high CPU frequency

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/fedehub/fmcFlexibleAutomation.git
   ```
2. Run *Coppeliasim*
   
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage


In the sketches below you can find the general design of my industrial cell 

![industrial cell][industrial-cell]

Since we were asked to make it "robot-centerd", all the conveyors have been placed accordingly, around the manipulator

![manipulator][md] 

Its charachteristichs are briefly shown in the image above

> Please, refer to the Docs folder for accessing the files containing all the skethces 


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Plant Layout design and simulation
  - [x] Import the parts model provided as mesh
  - [x] Based on the size of the parts, setupt the conveyors
  - [ ] Set up the floor shop like adding enclosures, modifying the visual aspects
  - [x] Programming part
    - [x] Program the motion of the conveyor
    - [x] Program the conveyor to spawn one of the three parts, randomly
- [x] Robot Simulation
  - [x] Based on your requirement of worksapce, select a type of mechanism
  - [x] Draw the schematic representation
  - [x] Using OOPs strategy, assemble your mechanism in CoppeliaSim
  - [x] Choose an appropriate gripper for all three parts (implement tool change if necessary)
  - [x] Implement the Inverse kinematics using the built in simIK API
  - [x] Implement **pick and place** logic, by using trajectory planning
  - [ ] Extend the logic above to pick the part and place  it in the right conveyor 
- [ ]Analysis and Optimization of the cell 
  - [ ] Ability to supply multiple vendors at the same time
  - [ ] Fully automated solution
  - [ ] Flexible in terms of Volune and mix product handling 
  - [ ] Zero-defect product 
 
    

See the [open issues](https://github.com/fedehub/fmcFlexibleAutomation/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement"

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. 

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Federico Civetta - s4194543@studenti.unige.it

Project Link: [https://github.com/fedehub/fmcFlexibleAutomation](https://github.com/fedehub/fmcFlexibleAutomation)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## List of resources

* [Official CoppeliaSim User Manual](https://coppeliarobotics.com)
* [Object Interactions](https://www.coppeliarobotics.com/helpFiles/en/designingDynamicSimulations.htm )
* [LUA manual reference](https://www.lua.org/manual/5.1/manual.html )
* [IDE](https://studio.zerobrane.com/)
* [Model of the engine parts](https://unigeit.sharepoint.com/sites/FLEXIBLEAUTOMATION2021/Documenti%20condivisi/Forms/AllItems.aspx?csf=1&web=1&e=B9YCQ1&cid=8d0e7acd%2D3a08%2D44ff%2Dad05%2D90045121c883&RootFolder=%2Fsites%2FFLEXIBLEAUTOMATION2021%2FDocumenti%20condivisi%2FModelForSimulationAssignment&FolderCTID=0x0120005FAF8D3B79DED14186C695672F8E587E)



<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->


[forks-shield]: 	https://img.shields.io/github/forks/fedehub/fmcFlexibleAutomation
[forks-url]: https://github.com/fedehub/fmcFlexibleAutomation/network/members
[stars-shield]: 	https://img.shields.io/github/stars/fedehub/fmcFlexibleAutomation
[stars-url]: https://github.com/fedehub/fmcFlexibleAutomation/stargazers
[issues-shield]: 	https://img.shields.io/github/issues/fedehub/fmcFlexibleAutomation
[issues-url]: https://github.com/fedehub/fmcFlexibleAutomation/issues
[license-shield]: https://img.shields.io/github/license/fedehub/fmcFlexibleAutomation
[industrial-cell]: https://github.com/fedehub/fmcFlexibleAutomation/blob/main/images/industrial-cell.png
[md]: https://github.com/fedehub/fmcFlexibleAutomation/blob/main/images/RRP_manipulator.png