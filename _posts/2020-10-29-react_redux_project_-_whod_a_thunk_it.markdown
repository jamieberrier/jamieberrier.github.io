---
layout: post
title:      "React Redux Project - Who'd A Thunk It?"
date:       2020-10-29 19:20:56 +0000
permalink:  react_redux_project_-_whod_a_thunk_it
---


It’s finally here! My final project! I knew I wanted to build some sort of game to diversify my project portfolio and challenge myself. But what? It hit me while enjoying a rare me-time moment playing my go-to game, Sudoku. Time to get started!

However, engaging in focused work time with a 2nd grader distance learning across the kitchen table was challenging to say the least. To help me maintain focus, I started playing nature sounds in my headphones while coding. I felt focused AND more relaxed. 💡 A Sudoku game with soothing nature sounds! Nadoku! 

Upon logging in, a user selects 1 of the 6 puzzle difficulties (easy to inhuman) and 1 nature sounds category (currently: ocean, rain forest, water, forest, rain). The user can then listen to the nature sounds playlist while solving the generated Sudoku puzzle. 🎶 🌊 🎶

I quickly realized the power of Redux’s unidirectional data flow when coding the puzzle grid. For example, when a user clicks on a number on the number pad, all occurrences of that number on the puzzle grid are highlighted. 

> The `onClick` event handler callback, `handleOnClick`, triggers the action creator `highlightCells` --> which dispatches the action `HIGHLIGHT_CELLS` to the reducer --> which returns the new state of the puzzle --> which causes the puzzle grid to re-render with highlighted cells (that lay in the house that Jack built). 

All in the blink of an eye!

Redux action creators don’t support asynchronous actions (e.g. fetching data). We need a middleman, er, middleware. Redux Thunk middleware lets us write action creators that return a function (a thunk) instead of a POJO. 

>A thunk is a function that wraps an expression to delay its evaluation. ([README.md](https://github.com/reduxjs/redux-thunk))  
>
> The term originated as a humorous, incorrect, past participle of "think". That is, a "thunk value" becomes available after its calculation routine is thought through, or executed. ([Wikipedia](https://en.wikipedia.org/wiki/Thunk))

Async actions, like API calls, return the thunk that the fetch request is wrapped in (`return dispatch => {}`), waiting until after the fetched data is available and then synchronously rendering the app.

![](https://media.giphy.com/media/xULW8rCSrt1JwaxTnW/giphy.gif)
