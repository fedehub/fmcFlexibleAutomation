<div id="top"></div>




<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]




<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/fedehub/fmcFlexibleAutomation">
    <img src="images/logo-black.png" alt="Logo" width="80" height="80">
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

- [ ] Plant layout simulation
- [x] robot simulation
- [ ] Analysis and optimization of the cell
- [ ] Report delivery


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

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.
In the sketches below you can find the general design of my ![industrial cell][industrial-cell]

Since we were asked to make it "robot-centerd", all the conveyors have been placed accordingly, around the ![manipulator][md]. Its charachteristichs are briefly shown in the image above

> Please, refer to the Docs folder for accessing the files containing all the skethces 


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [x] build manipulator model
- [x] Set up the industrial cell environment
- [x] Configure the conveyors
  - [x] place them
  - [x] save measures
- [ ] Integrate the manipulator model into the Industrial cell scene 
  - [ ] check the measures 
    

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

Distributed under the MIT License. See `LICENSE.txt` for more information.

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



<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/fedehub/fmcFlexibleAutomation/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/fedehub/fmcFlexibleAutomation/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/fedehub/fmcFlexibleAutomation/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/fedehub/fmcFlexibleAutomation/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/fedehub/fmcFlexibleAutomation/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[product-screenshot]: images/screenshot.png
[industrial-cell]: https://github.com/fedehub/fmcFlexibleAutomation/images/industrial-cell.png
[md]: https://github.com/fedehub/fmcFlexibleAutomation/images/RRP_manipulator.png