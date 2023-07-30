# [web accessibility](https://youtu.be/LH4Sn9ZF-jQ)

- what is web accessibility?
  - making website supportive for disable people and search engine
- how to check web accessibility?
  - inspect -> lighthouse -> accessibility
  - axe Devtools for accessibility testing
  - chromeVox for screen reading
- Tips for making website accessible:

1. Use Semantic elements over non semantic elements.

- semantic tags are meaningful tags for human, search engine. example: `<form> <header> <nav> <footer> <table> <p> <h1> etc.`
- non-semantic tags are not meaningful tags for human, search engine. example: `<span> <div> etc.`
- Use landmark -> header, nav, main, footer etc. landmarks helps to naviagte from one place to another.
- **Use this in code**: Semantic Elements: The `<div>` elements have been replaced with more appropriate semantic elements (`<nav>`, `<header>`, `<main>`, `<section>`, `<footer>`) to improve the structure and meaning of the content.

```html
<nav id="navbar" role="navigation" aria-label="Main Navigation">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#about">About Me</a></li>
    <li><a href="#tutorial">Tutorials</a></li>
    <li><a href="#contact">Contact Me</a></li>
  </ul>
</nav>
```

- You can explicitly make accessible by using role
- Example is given below:

  ```html
  <!-- not accessible example-->
  <div id="nav">navbar here</div>
  <div id="header">header here</div>
  <div id="main">main here</div>
  <div id="footer">footer here</div>
  <div>Click me</div>

  <!-- accessible example-->
  <nav id="nav">navbar here</nav>
  <header id="header">header here</header>
  <main id="main">main here</main>
  <footer id="footer">footer here</footer>
  <button>Click me</button>
  ```

- Example of explicit semantic vs implicit sematic element

  ```html
  <div role="button">Click me</div>
  <button>Click me</button>
  ```

2. Use Heading tags in order

- use one h1 element in a webpage
- keep sequence when using: h1 -> h2 -> h3 ... (follow top-down order)
- Example is given below:

  ```html
  <!-- not accessible example-->
  <h2>Anisul Islam</h2>
  <h1>Software developer</h1>
  <h3>Tampere, Finland</h3>

  <!-- accessible example-->
  <h1>Anisul Islam</h1>
  <h2>Software developer</h2>
  <h3>Tampere, Finland</h3>
  ```

3. Use alt attribute

- use alt attribute for `<img />` element
- alt attribute provides more info to the blind people
- low bandwidth might not render the image so the alt will help here
- alt attributes helps technologies like search engines
- title attribute can be used when we hover over image to get extra information
- example

  ```html
  <!-- not accessible example-->
  <img src="https://i.postimg.cc/X7YkHF12/ian.jpg" height="250" />

  <!-- accessible example-->
  <img
    src="https://i.postimg.cc/X7YkHF12/ian.jpg"
    height="250"
    alt="anisul islam profile image" />
  ```

4. Contrast ratio checker

   - use contrast ratio checker for foreground and background color: https://webaim.org/resources/contrastchecker/
   - example

   ```html
   <!-- not accessible example-->
   <a href="http://stduywithanis.com" target="_blank" style="color: gray"
     >visit</a
   >

   <!-- accessible example-->
   <a href="http://stduywithanis.com" target="_blank" style="color: black"
     >visit</a
   >
   ```

5. Declare the languages

   - `<html lang="en">`

6. Meaningful Link txt

   - make link text descriptive, understandable and clear
   - example

   ```html
   <!-- not accessible example-->
   <a href="http://stduywithanis.com" target="_blank">visit</a>

   <!-- accessible example-->
   <a href="http://stduywithanis.com" target="_blank"
     >Visit Anisul Islam's website</a
   >
   ```

7. Form related matters

   - use label and bind input elements with label by using id and for value same. example is given below:

     ```html
     <!-- not accessible example-->
     <div>
       Name:
       <input type="text" name="name" id="name" required />
     </div>

     <div>
       Email:
       <input type="email" name="email" id="email" required />
     </div>

     <div>
       <span>Choose Gender:</span>
       <input type="radio" id="male" name="gender" value="male" />
       <span>Male</span>

       <input type="radio" id="female" name="gender" value="female" />
       <span>Female</span>
     </div>

     <!-- accessible example-->
     <div>
       <label for="name">Name:</label>
       <input type="text" name="name" id="name" required />
     </div>

     <div>
       <label for="email"> Email:</label>
       <input type="email" name="email" id="email" required />
     </div>

     <div>
       <span>Choose Gender:</span>
       <input type="radio" id="male" name="gender" value="male" />
       <label for="male">Male</label>

       <input type="radio" id="female" name="gender" value="female" />
       <label for="female">Female</label>
     </div>
     ```

8. aria-label vs aria-labelby vs aria-escriptionby

   - these attribute has no visual impact but they are for assistive purpose. use them only when you can not use semantic elements
   - aria-label add accessible name directly to an element and it has higher priority than the element value. In
   - aria-descriptionby describes an element
   - aria-labelby create a relationship between elements
   - Example

   ```html
   <!-- not accessible example-->
   <button>Learn More</button>

   <!-- accessible example-->
   <button aria-label="Learn more about me">Learn more</button>

   <!-- not accessible example-->
   <div>
     Password:
     <input type="password" name="password" id="password" required />
     <div>(Pasword must be at least 8 character long)</div>
   </div>

   <!-- accessible example-->
   <div>
     <label for="password"> Password </label>
     <input
       type="password"
       name="password"
       id="password"
       aria-describedby="help"
       required />
     <div id="help">Pasword must be at least 8 character long</div>
   </div>

   <button aria-describedby="learn-more-desc">Learn More</button>
   <div id="learn-more-desc" class="sr-only">
     Click to learn more about Anisul Islam
   </div>

   <!-- not accessible example-->
   <h3>Hobbies</h3>
   <ul>
     <li>Playing Football</li>
     <li>Playing Badminton</li>
     <li>Swimming</li>
   </ul>

   <!-- accessible example-->
   <h3 id="hobbies">Hobbies</h3>
   <ul aria-labelledby="hobbies">
     <li>Playing Football</li>
     <li>Playing Badminton</li>
     <li>Swimming</li>
   </ul>
   ```

9. use role to make explicitly accessible, tabindex for keyboard navigation, default tabindex value is 0

   - example

     ```html
     <!-- not accessible example-->
     <div id="nav">
       <ul>
         <li><a href="#">Home</a></li>
         <li><a href="#">About</a></li>
         <li><a href="#">Contact</a></li>
       </ul>
     </div>

     <!-- accessible example-->
     <nav aria-label="navigation menu">
       <ul id="menubar" role="menubar" aria-label="navigation menu">
         <li role="none">
           <a href="#" role="menuitem" tabindex="0">Home</a>
         </li>
         <li role="none">
           <a href="#about" role="menuitem" tabindex="0">About</a>
         </li>
         <li role="none">
           <a href="#contact" role="menuitem" tabindex="0">Contact</a>
         </li>
       </ul>
     </nav>
     ```

10. make search engine friendly by using meta tag and also use lang=""

    - Example

    ```html
    <meta
      name="description"
      content="this website is about anisul islam's portfolio" />
    <meta name="keywords" content="anisul, portfolio" />
    ```

11. Provide Skip Links for Keyboard Navigation:

    Skip links allow users to bypass repetitive content and directly access the main content, especially helpful for keyboard-only users.
    Example:

```html
<a href="#main-content" class="skip-link">Skip to main content</a>
...
<main id="main-content">
  <!-- Main content goes here -->
</main>
```

12. Ensure Color Contrast for Readability:

    Maintain a sufficient contrast ratio between text and background colors to ensure readability for users with low vision.
    Example:

```html
<h1 style="color: #002b36; background-color: #b58900;">Heading</h1>
```

13. Use ARIA Roles for Non-Semantic Elements:

    Add ARIA roles to non-semantic elements to give them meaningful roles for assistive technologies.
    Example:

```html
<div role="button" tabindex="0">Click Me</div>
```

14. Provide Descriptive Link Text for Screen Readers:

    Use descriptive link text to provide context and clarity to screen reader users.
    Example:

```html
<a href="https://example.com" aria-label="Visit Example website">Visit Example</a>
```

15. Enable Keyboard Access for Interactive Elements:

    Ensure that all interactive elements, such as buttons and form elements, are keyboard accessible and focusable.
    Example:

```html
<button type="submit" tabindex="0">Submit</button>
```

- References:

  - https://www.w3.org/WAI/fundamentals/accessibility-intro/
  - https://www.w3schools.com/html/html_accessibility.asp

  <br/>
