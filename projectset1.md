# Project related to dom

## project related to dom

[Click here](https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

# Solution Code
### Project 1
``` javascript
console.log('Hii');
const button = document.querySelectorAll('.button');
const body = document.querySelector('body');

button.forEach(function (but) {
  console.log(but);
  but.addEventListener('click', function (e) {
    //console.log(e);
    //console.log(e.target);
    if (e.target.id === 'grey') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'white') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'blue') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'purple') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'yellow') {
      body.style.backgroundColor = e.target.id;
    }
  });
});

```
### Project 2
``` javascript
const form = document.querySelector('form');
form.addEventListener('submit', function (e) {
  e.preventDefault();
  const height = parseInt(document.querySelector('#height').value);
  const weight = parseInt(document.querySelector('#weight').value);
  const results = document.querySelector('#results');
  //console.log(results);

  if (height === '' || height < 0 || isNaN(height)) {
    results.innerHTML = 'Please give a valid height';
  } else if (weight === '' || weight < 0 || isNaN(weight)) {
    results.innerHTML = 'Please Enter a valid weight';
  } else {
    const bmi = (weight / ((height * height) / 10000)).toFixed(2);
    if (bmi <= 18.6) {
      results.innerHTML = `<span>${bmi} ->Under Weight</span>`;
    }
    if (bmi > 18.6 && bmi <= 24.9) {
      results.innerHTML = `<span>${bmi} ->Normal Weight Weight</span>`;
    } else {
      results.innerHTML = `<span>${bmi} ->Over Weight</span>`;
    }
  }
});
```
### Project 3
```javascript
const clock = document.getElementById('clock');

setInterval(function () {
  let date = new Date();
  //console.log(date.toLocaleTimeString());
  clock.innerHTML = date.toLocaleTimeString(date);
}, 1000);
```
### Project 4
```javascript
let num = parseInt(Math.random() * 100 + 1);
const submit = document.querySelector('#subt');
const userInpt = document.querySelector('#guessField');
const guessSlot = document.querySelector('.guesses');
const last = document.querySelector('.lastResult');
const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');
const p = document.createElement('p');
const remaining = document.querySelector('.lastResult');

let prevGuess = [];
let numOfGuess = 1;

let playGame = true;

if (playGame) {
  submit.addEventListener('click', function (e) {
    e.preventDefault();
    const guess = parseInt(userInpt.value);
    console.log(guess);
    ValidateGuess(guess);
  });
}

function ValidateGuess(guess) {
  if (isNaN(guess)) {
    alert('Please Enter a valid Number');
  } else if (guess < 1) {
    alert('Please Enter a Number >1');
  } else if (guess > 100) {
    alert('Please Enter a Number <100');
  } else {
    prevGuess.push(guess);
    if (numOfGuess === 11) {
      displayGuess(guess);
      displayMsg(`Game Over. Random Number was ${num}`);
      endGame();
    } else {
      displayGuess(guess);
      checkGuess(guess);
    }
  }
}

function checkGuess(guess) {
  if (guess == num) {
    displayMsg(`You have guessed it right`);
    endGame();
  } else if (guess < num) {
    displayMsg(`Number is TOOO Low`);
  } else {
    displayMsg(`Number is TOOO High`);
  }
}

function displayGuess(guess) {
  userInpt.value = '';
  guessSlot.innerHTML += `${guess} ,`;
  numOfGuess++;
  remaining.innerHTML = `${10 - numOfGuess}`;
}

function displayMsg(msg) {
  lowOrHi.innerHTML = `${msg}`;
}

function newGame() {
  const newGameButton = document.querySelector('#NewGame');
  newGameButton.addEventListener('click', function (e) {
    num = parseInt(Math.random() * 100 + 1);
    prevGuess = [];
    numOfGuess = 10;
    guessSlot.innerHTML = '';
    remaining.innerHTML = '';
    userInpt.removeAttribute('disable');
    startOver.removeChild(p);
  });
}

function endGame() {
  userInpt.value = '';
  userInpt.setAttribute('disable', '');
  p.classList.add('button');
  p.innerHTML = `<h2 id='NewGame'>Start New Game</h2>`;
  startOver.appendChild(p);
  newGame();
}

```
