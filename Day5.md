## Day5 :Data Fetching & Promises,*Destructuring Data,Async,Wrapping up
In summary, during Day 5 of my learning journey, I focused on important concepts and techniques in JavaScript:

**Data Fetching & Promises:** I learned to fetch data from APIs using the Fetch API, handle responses, and work with JSON data. Promises were introduced as a way to manage asynchronous operations and control data flow.

**Destructuring Data:** Destructuring syntax allowed me to extract specific values from objects or arrays and assign them to variables. This improved code readability and efficiency.

**Async:** I explored asynchronous programming using async functions and the `await` keyword. This provided a more synchronous-like syntax for managing asynchronous code, making it easier to understand and work with.

**Modules:** I studied JavaScript modules, which helped me organize my code into smaller, reusable pieces. I learned how to import and export functions, variables, and classes between modules, facilitating modular architecture and code sharing.

**Wrapping up:** I took the opportunity to review the key concepts and techniques covered throughout my learning journey, solidifying my understanding of JavaScript fundamentals, DOM manipulation, event handling, data types, functions, and advanced topics such as data fetching, destructuring, async programming, and modules.
# example
```javascript
<!DOCTYPE html>
<!-- saved from url=(0068)https://anjana.dev/javascript-first-steps/3-doggofetch-finished.html -->
<html lang="en-US"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Doggo Fetch</title>
    <style>
        body {
            margin: 1rem auto;
            padding: 3rem;
            font-family: sans-serif;
        }
        header {
            width: 70%;
            margin: 1em auto;
        }
        main {
            max-width: 70%;
            margin: 0px auto;
            display:flex; 
            flex-direction: column;
        }
        img {
            max-width: 100%;
        }
        #image-frame {
            font-size: x-large;
            text-align: center;
            margin: 1rem auto;
        }
        #explanation, #score {
            padding: 1rem;
            text-align: center;
        }
        #options {
            max-width: 100%;
            display: flex;
            flex-direction: column;
        }
        button {
            padding: 0.5rem;
            font-size: medium;
            border-radius: 5px;
        }
        .correct {
            background-color: lightgreen;
        }
        .incorrect {
            background-color: lightpink;
        }
        .hidden {
            display: none;
        }
    </style>
  </head>
  <body data-new-gr-c-s-check-loaded="14.1114.0" data-gr-ext-installed="">
    <header>
    <h1>Guess the Doggo</h1>
    <p>What breed is the dog in this image?</p>

    </header>

    <main>
    <div id="image-frame"><img src="./Doggo Fetch2_files/n02110958_12120.jpg"></div>
    <div id="options">
    <button name=" pug" value=" pug" class="correct"> pug</button><button name="brabancon" value="brabancon">brabancon</button><button name="english mastiff" value="english mastiff">english mastiff</button></div>

    </main>

  


  <script type="module">

    const RANDOM_IMG_ENDPOINT = "https://dog.ceo/api/breeds/image/random";

    const BREEDS = ["affenpinscher", "african", "airedale", "akita", "appenzeller", "shepherd australian", "basenji", "beagle", "bluetick", "borzoi", "bouvier", "boxer", "brabancon", "briard", "norwegian buhund", "boston bulldog", "english bulldog", "french bulldog" "otterhound"];
    
    // Utility function to get a randomly selected item from an array
    function getRandomElement(array) {
        const i = Math.floor(Math.random() * array.length);
        return array[i];
    }

    // Utility function to shuffle the order of items in an array in-place
    function shuffleArray(array) {
        return array.sort((a,b) => Math.random() - 0.5);
    }



    // TODO 1
    // Given an array of possible answers, a correct answer value, and a number of choices to get,
    // return a list of that many choices, including the correct answer and others from the array
    function getMultipleChoices(n, correctAnswer, array) {
        // Use a while loop and the getRandomElement() function
        // Make sure there are no duplicates in the array
        const choices = [correctAnswer];
        while (choices.length < n) {
            let candidate = getRandomElement(array);
            if (choices.indexOf(candidate) < 0) { // check if this is already in the array
                choices.push(candidate); // if not, add it
            }
        }
        return shuffleArray(choices);
    }

    
    // TODO 2
    // Given a URL such as "https://images.dog.ceo/breeds/poodle-standard/n02113799_2280.jpg"
    // return the breed name string as formatted in the breed list, e.g. "standard poodle"
    function getBreedFromURL(url) {
        // The string method .split(char) may come in handy
        // Try to use destructuring as much as you can
        const [,path] = url.split("/breeds/");
        const [breedID] = path.split("/");
        const [breed, subtype] = breedID.split("-");
        return [subtype, breed].join(" ");
    }



    // TODO 3
    // Given a URL, fetch the resource at that URL, 
    // then parse the response as a JSON object,
    // finally return the "message" property of its body
    async function fetchMessage(url) {
        const response = await fetch(url);  // Fetch the resource at the given URL
        const {message} = await response.json(); // Parse the response as JSON & remember its 'message' value
        return message; // Return the message
    }


    // Function to add the multiple-choice buttons to the page
    function renderButtons(choicesArray, correctAnswer) {

        // Event handler function to compare the clicked button's value to correctAnswer
        // and add "correct"/"incorrect" classes to the buttons as appropriate
        function buttonHandler(e) {
            if (e.target.value === correctAnswer) {
                e.target.classList.add("correct");
            } else {
                e.target.classList.add("incorrect");
                document.querySelector(`button[value="${correctAnswer}"]`).classList.add("correct");
            }
        }

        const options = document.getElementById("options"); // Container for the multiple-choice buttons

        // TODO 4
        // For each of the choices in choicesArray,
        // Create a button element whose name, value, and textContent properties are the value of that choice,
        // attach a "click" event listener with the buttonHandler function,
        // and append the button as a child of the options element
        choicesArray.map(choice => {
            let button = document.createElement("button");
            button.value = button.name = button.textContent = choice;
            button.addEventListener("click", buttonHandler);
            options.appendChild(button);
        })
    }


    // Function to add the quiz content to the page
    function renderQuiz(imgUrl, correctAnswer, choices) {
        const image = document.createElement("img");
        image.setAttribute("src", imgUrl);
        const frame = document.getElementById("image-frame");

        image.addEventListener("load", () => {
            // Wait until the image has finished loading before trying to add elements to the page
            frame.replaceChildren(image);
            renderButtons(choices, correctAnswer);
        })
        
    }

    // Function to load the data needed to display the quiz
    async function loadQuizData() {
        document.getElementById("image-frame").textContent = "Fetching doggo...";
        
        const doggoImgUrl = await fetchMessage(RANDOM_IMG_ENDPOINT);
        const correctBreed = getBreedFromURL(doggoImgUrl);
        const breedChoices = getMultipleChoices(3, correctBreed, BREEDS);

        return [doggoImgUrl, correctBreed, breedChoices];
    }

    // TODO 5
    // Asynchronously call the loadQuizData() function,     
    // Then call renderQuiz() with the returned imageUrl, correctAnswer, and choices 
    const [imageUrl, correctAnswer, choices] = await loadQuizData();
    renderQuiz(imageUrl, correctAnswer, choices);
    


  </script>

</body><grammarly-desktop-integration data-grammarly-shadow-root="true"><template shadowrootmode="open"><style>
  div.grammarly-desktop-integration {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select:none;
    user-select:none;
  }

  div.grammarly-desktop-integration:before {
    content: attr(data-content);
  }
```
# Exercise
```javascript

const characterListElement = document.getElementById('characterList');

async function fetchCharacterData() {
  try {
    const response = await fetch('https://rickandmortyapi.com/api/character?status=alive');
    if (!response.ok) {
      throw new Error('Failed to fetch character data');
    }
    const data = await response.json();
    const characters = data.results.slice(0, 50); // Limit to first 50 characters

    characters.forEach(character => {
      const li = document.createElement('li');
      const image = document.createElement('img');
      const name = document.createElement('p');
      const location = document.createElement('p');
      const species = document.createElement('p');
      const gender = document.createElement('p');

      image.src = character.image;
      name.textContent = `Name: ${character.name}`;
      location.textContent = `Location: ${character.location.name}`;
      species.textContent = `Species: ${character.species}`;
      gender.textContent = `Gender: ${character.gender}`;

      li.appendChild(image);
      li.appendChild(name);
      li.appendChild(location);
      li.appendChild(species);
      li.appendChild(gender);

      characterListElement.appendChild(li);
    });
  } catch (error) {
    console.error(error);
    characterListElement.textContent = 'Error fetching character data';
  }
}

fetchCharacterData();


```
