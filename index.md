---
layout: base
title: John Tab 
hide: true
---

### Me and Team

Hi! My name is Sophie.

# Popcorn Hack 1
## Within the first code cell, here is my edited code! -->  In a juypter notebook file, you can run this code in developer tools console!
%%javascript
// Step 1: Make some variables
let name = "Sam";
let age = 10;

// Step 2: Print a message
console.log("Hi, my name is", name);
console.log("I am", age, "years old.");

// Step 3: Unfinished part
// TODO: Make a new variable called "nextYearAge"
// that is the age plus 1
let nextYearAge = age + 1;

// let nextYearAge = ???   // <-- finish this line!

// TODO: Print out the result
// Example: "Next year I will be 11 years old."
console.log("Next year I will be 11 years old"); // <-- finish this line!

# Popcorn Hack 2
## Within the second code cell, here is my edited code! --> In a juypter notebook file, you can run this code in developer tools console!
%%javascript
// Step 1: Define the Animal class
class Animal {
  // Initialize each animal with a name, sound, and type
  constructor(Buddy, bark, dog) {
    this.name = Buddy;
    this.sound = bark;
    this.kind = dog;
  }

  // Make the animal speak
  speak() {
    console.log(`${this.name} the ${this.kind} says ${this.sound}!`);
  }

  // Bonus method: describe the animal
  describe() {
    console.log(`${this.name} is a ${this.kind} and is very aggresive!`);
  }
}

// Step 2: Create a list to hold all the animals in the zoo
let zoo = [];

// Step 3: Add animals to the zoo
// TODO: Create at least 3 animals and push them into the zoo array
// Example:
zoo.push(new Animal("Buddy", "Woof", "Dog"));
zoo.push(new Animal("Cowabunga", "Meow", "Cat"));
zoo.push(new Animal("Polly", "Squawk", "Parrot"));

// Step 4: Loop through all animals and make them speak
// TODO: Use a for loop (or forEach) to call speak() on each animal
zoo.forEach(animal => {
  animal.speak();
  // Step 5: Optional bonus: Call describe() too
  animal.describe();
});

// Step 5 Bonus: Let the user add a new animal (works in browser)
// Uncomment if running in browser with prompt()
let name = prompt("Bob:");
let sound = prompt("rawr:");
let kind = prompt("the builder:");
let newAnimal = new Animal(name, sound, kind);
zoo.push(newAnimal);
newAnimal.speak();
newAnimal.describe();

# Homework Finished Project
## Within the third and final code cell, here is my edited code! -->

%%javascript
// Step 1: Make a list of choices
const choices = ["rock", "paper", "scissors"];

// Step 2: Ask the user for their choice (browser version with prompt)
let userChoice = prompt("Choose rock, paper, or scissors:").toLowerCase();

// Step 3: Computer picks a random choice
const computerChoice = choices[Math.floor(Math.random() * choices.length)];
console.log("Computer chose:", computerChoice);

// Step 4: Compare userChoice and computerChoice
if (userChoice === computerChoice) {
    console.log("It's a tie!");
  } else if (
    (userChoice === "rock" && computerChoice === "scissors") ||
    (userChoice === "scissors" && computerChoice === "paper") ||
    (userChoice === "paper" && computerChoice === "rock")
  ) {
    console.log("You win!");
  } else if (
    userChoice === "rock" ||
    userChoice === "paper" ||
    userChoice === "scissors"
  ) {
    console.log("You lose!");
  } else {
    console.log("Invalid choice! Please choose rock, paper, or scissors.");
  }

// Bonus: Put the whole game in a loop
while (true) {
  // Step 2: Ask the user for their choice (browser version with prompt)
  let userChoice = prompt("Choose rock, paper, or scissors:").toLowerCase();

  // If the user clicks "Cancel" or leaves it blank, stop the game
  if (!userChoice) {
    console.log("Game ended. Thanks for playing!");
    break;
  }
// Uncomment to play multiple rounds in browser
/*
while (true) {
  let userChoice = prompt("Choose rock, paper, or scissors”)


## Links to Learning

### Development Environment

> Coding starts with tools, explore these tools and procedures with a click.

<a href="https://github.com/Open-Coding-Society/student">
    <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub">
</a>
<a href="https://open-coding-society.github.io/student">
    <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?logo=github&logoColor=white" alt="GitHub Pages">
</a>
<a href="https://kasm.opencodingsociety.com/" class="button small" style="background-color: #6b4bd3ff">
    KASM
</a>
<a href="https://vscode.dev/" class="button small" style="background-color: #d38a4bff">
    <span style="color: #FFFFFF">VSCODE</span>
</a>

<br>

### Class Progress

<a href="{{site.baseurl}}/snake" class="button small" style="background-color: #6b4bd3ff">
    Snake Game
</a>
<a href="{{site.baseurl}}/turtle" class="button small" style="background-color: #2A7DB1">
    <span style="color: #000000">Turtle</span>
</a>

<br>

<!-- Contact Section -->
### Get in Touch

> Feel free to reach out if you'd like to collaborate or learn more about our work.

<p style="color: #2A7DB1;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #2A7DB1; text-decoration: underline;">Socials</a></p>
