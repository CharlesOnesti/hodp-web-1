# Personal Assistant™ Web App

To run the App, first install the required dependencies with `npm i`. Then, just type `npm run dev` into the terminal, and then go to [http://localhost:3000](http://localhost:3000) to view it in the browser. To get linting working, make sure you open VSCode with the personal-assistant folder at the top level (`code personal-assistant`), and work from there.


### App Planning

Before we start coding, we should plan out how we want our app to look. For now, however, think about implementing only the Todos page with the following functionality:

1. Keep a list of todos (just a simple string description)
2. Add todos to a list
3. Delete todos once they have been added
4. Search through Todos by substring

Here are some more details:
- When there are no todos in the list (either because you haven't added any or the search has yielded no results), some special text should render instead of the list
- As soon as a todo has been added, it should immediately appear as a list element under your Todos. Next to the todo should be a button which deletes the todo from the list.
- The search bar updates the filtering whenever its text is changed - if a todo does not contain the text as a substring then it is not rendered in the list
- At this state of the project, do not worry about styling at all (that will be the next stage!)--for now, it's most important that you nail down the basics of data flow and state management in React. Also, if you have any ideas for additional functionality that you want to add, please go ahead!! You do not have to conform to the example app in any meaningful way besides implementing a Todo list.

#### How to Plan

You might find [Thinking in React](https://reactjs.org/docs/thinking-in-react.html) to be a helpful example. That page uses React Classes to build components, which are an old way of managing state in React. Don't worry about emulating that specifically, just follow along with the process and use the methods we've learned in lecture.

Regardless of your background in React, we can break down this task. Let's outline in high-level terms a guideline for implementing the functionality of the app.

1. Breaking the user interface into different components.

- I like to think of a component in React as a subset of the user interface which accomplishes one thing--for example, the "Add Todo" Bar, the bulleted list of Todos, or the search bar.
- Furthermore, break up each component into potential subcomponents and ultimately React tags such as div, ul, or input.
- It's often very helpful to draw out the user interface by hand and use the 'box' method to group individual sections into components and then sub components.

2. Now that you've established which components your app will use, consider how data should flow through your application. We can break this up into a few smaller questions.

- What type of data needs to be stored in the app? Certainly you will want some sort of a list of todos, but what form should those todos take? A list of strings? A list of objects containing a string and an ID? Do keep in mind that you will have to have a way of uniquely identifying each todo so that it can individually be deleted from the list. If you choose to add IDs to your Todos, I would suggest looking at [nanoid](https://www.npmjs.com/package/nanoid). You can install it will `npm i --save nanoid`.
- What type of data does each component need to access? For example, if you decide to create a separate component for the unordered list of todos, that component will need to access the list of todos that you've stored somewhere in your app. Keep in mind that data flow in React is always downward--data in one component can be passed down to its child components through props, yet not vice versa. Therefore, if data needs to be accessed by two components, it needs to be stored in a common ancestor of those two components.

**Stretch Task:** Get started using real React components! Try rebuilding a page of your Personal website with React. You can just work directly off of the component in App.js. Run `npm run dev` to see the app in your browser.

### Styling

Now that we've learned how to use Styled Components, lets build some basic components that we'll use in our Personal Assistant. To help us in the development process, we're going to use Storybook, a development tool which can help us view components in isolation and in different states.

I've included one example component under `/src/ExampleComponent`, which you can use as a template when creating new components. 

Start by building the components that you planned. Try passing test data to your components and make sure they work correctly in all states (e.g. write a fake list of todos and pass it to your todo list component).

**Stretch Task:** Make your components fully responsive using media queries! Also try adding hover states and transitions.

### Adding Functionality

With the help of state, we can finally store and manage our Todos dynamically. Now, use useReducer (or useState) to implement the todos state and useState and track any inputs you've made.

**Stretch Task:** Abstract your Todo state management with the Context API. React Context will allow you to access the same state across multiple pages--essentially anywhere in your App. This is quite difficult. Here's a [good article](https://www.taniarascia.com/using-context-api-in-react/) to get you started. Instead of passing that 'user' object, as is done in the example, pass the state and setState variables returned by useReducer.

### Deployment

If you want to deploy your app to Github Pages, follow the steps below:
1. In your browser, go to your github page and create a new repository with the name of your app--maybe something like `personal-assistant`. You can make it public or private, but don't initialize it with a README.
2. Once you've made it, copy the link to clone the repo. In your terminal, `cd` into your personal-assistant app and type
```sh
git init
git remote add origin <YOUR_REPO_URL>
```
3. Also in your app, in your package.json file there should be a "hompage" attribute. Format it with your credentials, replacing `<GITHUB_USERNAME>` and `<APP_NAME>`. In my case, it looked like `"homepage": "http://CharlesOnesti.github.io/hodp-web-1"`.
4. You should now be able to publish a production version of your app to that repository by simply typing `npm run deploy`. This might take a minute to finish, but the output should give you the URL to your new personal assistant web app! Try adding it as the home page of your browser to be greeted every time you go online!
