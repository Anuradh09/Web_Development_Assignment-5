1.  Difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll:

    getElementById("id")
    Selects a single element by its unique id.
    Returns one element (or null if not found).

    Example:
    let el = document.getElementById("header");
    getElementsByClassName("class")
    Selects all elements with a specific class name.
    Returns an HTMLCollection (live list, updates if DOM changes).

    Example:
    let items = document.getElementsByClassName("item");
    querySelector("cssSelector")
    Selects the first matching element using a CSS selector.

    Example:
    let el = document.querySelector(".item"); // first element with class "item"
    querySelectorAll("cssSelector")
    Selects all matching elements using a CSS selector.
    Returns a NodeList (not live).

    Example:
    let items = document.querySelectorAll(".item");

2.  How to create and insert a new element into the DOM:

    Steps:
    Create a new element with document.createElement()
    Set content or attributes (textContent, innerHTML, setAttribute)
    Append it to the desired parent (appendChild, append, prepend, insertBefore)

    Example:
    let newDiv = document.createElement("div");
    newDiv.textContent = "Hello, World!";
    newDiv.setAttribute("class", "box");

    // Append to body
    document.body.appendChild(newDiv);

3.  What is Event Bubbling and how does it work?

    Event Bubbling means when an event occurs on an element, it first runs the event handlers on that element, then on its parent, then on the parent’s parent, and so on up to the root (document).

    Example: Clicking a button inside a <div> will trigger:
    Button’s event handler
    Then <div>’s handler
    Then <body>, <html>, and finally document

    document.getElementById("btn").addEventListener("click", () =>
    {
    console.log("Button clicked");
    });
    document.getElementById("container").addEventListener("click", () =>
    {
    console.log("Container clicked");
    });
    If button is clicked both logs will appear due to bubbling.

4.  What is Event Delegation? Why is it useful?

    Event Delegation is a technique where you attach a single event listener to a parent element instead of multiple child elements.
    When an event bubbles up, the parent detects which child triggered it using event.target.

    Why useful?
    Better performance (fewer event listeners in memory).
    Handles dynamically added elements without re-assigning listeners.

    Example:
    document.getElementById("list").addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
    console.log("Clicked:", e.target.textContent);
    }
    });
    Even if new <li> items are added later, the parent <ul> can still handle clicks.

5.  Difference between preventDefault() and stopPropagation():

    preventDefault()
    Prevents the default browser action of an event.

    Example:
    Stops form submission or prevents a link from opening.

    document.querySelector("form").addEventListener("submit", (e) =>
    {
    e.preventDefault(); // stop form from submitting
    });

    stopPropagation()
    Stops the event from bubbling up (or capturing down).

    Example:
    Prevents parent elements’ event handlers from running.

    document.getElementById("btn").addEventListener("click", (e) =>
    {
    e.stopPropagation(); // event won’t bubble to parent
    });
