<div id="top"></div>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
[![Forks][forks-shield]][forks-url]
-->


<!-- PROJECT LOGO -->
<br />
<h1 align="center">CTC Python Style Guide</h1>
  <p align="center">
    A set of code style and formatting guidelines for python projects created by the CTC R&D team.
    <br />
    Includes pythonic best practices, idioms, conventions, structure, and symbology. 
    <br />
    <br />
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#zen-of-python">Zen of Python</a></li>
    <li>
      <a href="#best-practices">Best Practices</a>
      <ul>
        <li><a href="#explicit-code">Explicit code</a></li>
        <li><a href="#one-statement-per-line">One statement per line</a></li>
        <li>
          <a href="#function-arguments">Function Arguments</a>
          <ul>
            <li><a href="#positional-arguments">Positional arguments</a></li>
            <li><a href="#keyword-arguments">Keyword arguments</a></li>
            <li><a href="#arbitrary-argument-list">Arbitrary argument list</a></li>
            <li><a href="#arbitrary-keyword-argument-dictionary">Arbitrary keyword argument dictionary</a></li>
          </ul>
        </li>
        <li><a href="#returning-values">Returning values</a></li>
      </ul>
    </li>
    <li>
      <a href="#idiomatic-python">Idiomatic Python</a>
      <ul>
        <li><a href="#unpacking">Unpacking</a></li>
        <li><a href="#create-ignored-variable">Create an ignored variable</a></li>
        <li>
          <a href="#list-construction">List Construction</a>
          <ul>
            <li><a href="#create-length-n-list-of-same-thing">Create a length-N list of the same thing</a></li>
            <li><a href="#create-length-n-list-of-lists">Create a length-N list of lists</a></li>
            <li><a href="#create-string-from-list">Create a string from a list</a></li>
          </ul>
        </li>
        <li><a href="#searching-for-item-in-collection">Searching for an item in a collection</a></li>
      </ul>
    </li>
    <li>
      <a href="#conventions">Conventions</a>
      <ul>
        <li><a href="#check-if-variable-equals-constant">Check if a variable equals a constant</a></li>
        <li><a href="#access-dictionary-element">Access a Dictionary Element</a></li>
        <li>
          <a href="#list-usage">List Usage</a>
          <ul>
            <li><a href="#short-ways-to-manipulate-lists">Short ways to manipulate lists</a></li>
            <li><a href="#filtering-list">Filtering a list</a></li>
            <li><a href="#possible-side-effects-of-modifying-original-list">Possible side effects of modifying the original list</a></li>
            <li><a href="#modifying-values-in-list">Modifying the values in a list</a></li>
          </ul>
        </li>
        <li><a href="#read-from-file">Read from a file</a></li>
        <li><a href="#line-continuations">Line continuations</a></li>
      </ul>
    </li>
    <li>
      <a href="#pep-8">PEP 8</a>
      <ul>
        <li><a href="#personal-preference-deviations">Personal preference deviations</a></li>
      </ul>
    </li>
    <li>
      <a href="#structure-and-formatting">Structure and Formatting</a>
      <ul>
        <li><a href="#code-map">Code map</a></li>
        <li><a href="#we-are-all-responsible-users">We are all responsible users</a></li>
        <li>
          <a href="#symbology">Symbology</a>
          <ul>
            <li><a href="#PLACEHOLDER">PLACEHOLDER</a></li>
          </ul>
        </li>
      </ul>
    </li>
    
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>


Zen of Python
Best Practices
  Explicit code
  One statement per line
  Function arguments
    Positional arguments
    Keyword arguments
    Arbitrary argument list
    Arbitrary keyword argument dictionary
  Returning values
Idiomatic Python - Writing Pythonic code
  Unpacking
  Create an ignored variable
  List construction
    Create a length-N list of the same thing
    Create a length-N list of lists
    Create a string from a list
  Searching for an item in a collection
Conventions
  Check if a variable equals a constant
  Access a Dictionary Element
  List Usage
    Short Ways to Manipulate Lists
    Filtering a list
    Possible side effects of modifying the original list
    Modifying the values in a list
  Read From a File
  Line Continuations
PEP 8
  Personal preference deviations
Structure and Formatting
  Code Map
  We are all responsible users
  Symbology


<!-- ABOUT THE PROJECT -->
## Zen of Python

[![Product Name Screen Shot][product-screenshot]](https://example.com)

Here's a blank template to get started: To avoid retyping too much info. Do a search and replace with your text editor for the following: `github_username`, `repo_name`, `twitter_handle`, `linkedin_username`, `email_client`, `email`, `project_title`, `project_description`

<p align="right">(<a href="#top">back to top</a>)</p>




<div class="section" id="explicit-code">
<h3>Explicit code<a class="headerlink" href="#explicit-code" title="Permalink to this headline">¶</a></h3>
<p>While any kind of black magic is possible with Python, the
most explicit and straightforward manner is preferred.</p>
<p><strong>Bad</strong></p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">def</span> <span class="nf">make_complex</span><span class="p">(</span><span class="o">*</span><span class="n">args</span><span class="p">):</span>
    <span class="n">x</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="n">args</span>
    <span class="k">return</span> <span class="nb">dict</span><span class="p">(</span><span class="o">**</span><span class="nb">locals</span><span class="p">())</span>
</pre></div>
</div>
<p><strong>Good</strong></p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">def</span> <span class="nf">make_complex</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">{</span><span class="s1">'x'</span><span class="p">:</span> <span class="n">x</span><span class="p">,</span> <span class="s1">'y'</span><span class="p">:</span> <span class="n">y</span><span class="p">}</span>
</pre></div>
</div>
<p>In the good code above, x and y are explicitly received from
the caller, and an explicit dictionary is returned. The developer
using this function knows exactly what to do by reading the
first and last lines, which is not the case with the bad example.</p>
</div>



### Built With

* [![Next][Next.js]][Next-url]
* [![React][React.js]][React-url]
* [![Vue][Vue.js]][Vue-url]
* [![Angular][Angular.io]][Angular-url]
* [![Svelte][Svelte.dev]][Svelte-url]
* [![Laravel][Laravel.com]][Laravel-url]
* [![Bootstrap][Bootstrap.com]][Bootstrap-url]
* [![JQuery][JQuery.com]][JQuery-url]

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* npm
  ```sh
  npm install npm@latest -g
  ```

### Installation

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
   ```sh
   git clone https://github.com/github_username/repo_name.git
   ```
3. Install NPM packages
   ```sh
   npm install
   ```
4. Enter your API in `config.js`
   ```js
   const API_KEY = 'ENTER YOUR API';
   ```

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3
    - [ ] Nested Feature

See the [open issues](https://github.com/github_username/repo_name/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

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

Your Name - [@twitter_handle](https://twitter.com/twitter_handle) - email@email_client.com

Project Link: [https://github.com/github_username/repo_name](https://github.com/github_username/repo_name)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
