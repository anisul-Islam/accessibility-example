# [web accessibility](https://youtu.be/LH4Sn9ZF-jQ)

- what is web accessibility?
  - making website supportive for disable people and search engine
- how to check web accessibility?
  - inspect -> lighthouse -> accessibility
  - axe Devtools for accessibility testing
  - chromeVox for screen reading
- Tips for making website accessible:

  1. Use Semantic elements over non semantic elements.

  - semantic tags are meaningful tags for human, search engine. example: `<form> <table> <p> <h1> etc.`
  - non-semantic tags are not meaningful tags for human, search engine. example: `<span> <div> etc.`
  - In the following example button is more accessible than div for making a button. Semantic elements help the screen readers.

  ```html
  <div>Click me</div>
  <button>Click me</button>
  ```

  - Example of explicit semantic vs implicit sematic element

  ```html
  <div role="button">Click me</div>
  <button>Click me</button>
  ```

  - landmarks helps to naviagte from one place to another: header, h1...h6, main, nav, footer

  2. Use Heading tags in order

  - use one h1 element in a webpage
  - keep sequence when using: h1 -> h2 -> h3 ... (follow top-down order)

  3. Use alt attribute

  - use alt attribute for `<img />` element
  - alt attribute provides more info to the blind people
  - low bandwidth might not render the image so the alt will help here
  - alt attributes helps technologies like search engines
  - title attribute can be used when we hover over image to get extra information

  4. Contrast ratio checker

  - use contrast ratio checker for foreground and background color: https://webaim.org/resources/contrastchecker/

  5. Declare the languages

  - `<html lang="en">`

  6. Meaningful Link txt

  - make link text descriptive, understandable and clear `<a href="http://studywithanis.com" target="_blank"> Visit Anisul Islam's website </a>`

  7. Form related matters

  - use label and bind input elements with label by using id and for value same. example is given below:

    ```html
    <label for="email">Email: </label> <input type="email" id="email" />

    <div class="form-control">
      <fieldset>
        <legend>Choose Gender:</legend>
        <div class="form-control">
          <input type="radio" id="male" name="gender" value="male" />
          <label for="male">Male</label>
        </div>
        <div class="form-control">
          <input type="radio" id="female" name="gender" value="female" />
          <label for="female">Female</label>
        </div>
      </fieldset>
    </div>
    ```

  8.  use aria-label vs aria-labelby vs aria-descriptionby

  - these attribute has no visual impact but they are for assistive purpose. use them only when you can not use semantic elements
  - The aria-label and aria-labelledby attributes are both used to give an element it's accessible name.
  - using forms with standards labels - you shouldn't need it at all: -> label, for is more than enough
  - aria-label add accessible name directly to an element and it has higher priority than the element value. In  
    the following example screen reader will say learn more about me instead of learn more
    `html <button aria-label="Learn more about me"> Learn more </button> `
  - aria-labelby create a relationship between elements

    ```html
    <h3 id="hobbies">Hobbies</h3>
    <ul aria-labelledby="hobbies">
      <li>Playing Football</li>
      <li>Playing Badminton</li>
      <li>Swimming</li>
    </ul>
    ```

    ```

    ```

  - aria-descriptionby
    ```html
    <div>
      <label for="password"> Password </label>
      <input
        type="password"
        name="password"
        id="password"
        aria-describedby="help"
        required
      />
      <div id="help">Pasword must be at least 8 character long</div>
    </div>
    ```

  9. role and tabindex -> tabindex can start from 0 then -1, -2 for lesser priority so that you can navigate by keyboard one after one in an order

  ```html
  <!-- use nav, role, tabindex, aria-label for an accessible navbar  -->

  <!-- NOT ACCESSIBLE -->
  <div id="nav">
    <a href="#">Home</a>
    <a href="#about">About Me</a>
    <a href="#tutorial">Tutorials</a>
    <a href="#contact">Contact Me</a>
  </div>

  <!-- ACCESSIBLE  -->
  <nav aria-label="navigation menu">
    <ul id="menubar" role="menubar" aria-label="navigation menu">
      <li role="none">
        <a href="#" role="menuitem" tabindex="-1">Home</a>
      </li>
      <li role="none">
        <a href="#about" role="menuitem" tabindex="-1">About Me</a>
      </li>
      <ul role="menu" aria-label="tutorials">
        <li role="none">
          <a href="#tutorials" role="menuitem" tabindex="0">Tutorials</a>
          <ul>
            <li role="none">
              <a href="#html" role="menuitem" tabindex="-1">HTML</a>
            </li>
            <li role="none">
              <a href="#css" role="menuitem" tabindex="-1">CSS</a>
            </li>
          </ul>
        </li>
      </ul>
      <li role="none">
        <a href="#contact" role="menuitem" tabindex="-1">Contact Me</a>
      </li>
    </ul>
  </nav>
  ```

- References:
- https://www.w3.org/WAI/fundamentals/accessibility-intro/
- https://www.w3schools.com/html/html_accessibility.asp

  <br/>
