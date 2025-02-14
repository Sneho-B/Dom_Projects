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