# Cat Tinder Testing with Jest and Enzyme

#### Overview
There are two main tools you'll use to test your React applications: Jest and Enzyme. Jest is a JavaScript testing framework that is added to React when you use the command `yarn create react-app`. Enzyme is a JavaScript testing utility for React that renders the components allowing the developer to test the component output.

#### Previous Lecture (1 hour 18 min)
[![YouTube](http://img.youtube.com/vi/J7VADNiI8Pk/0.jpg)](https://www.youtube.com/watch?v=J7VADNiI8Pk)

#### Learning Objectives
- can define Jest and Enzyme
- can implement an automated test suite
- can ensure components render properly
- can import and define dependencies in a test suite

#### Vocabulary
- Jest
- Enzyme
- Shallow rendering

#### Additional Resources
- [Jest Matchers](https://facebook.github.io/jest/docs/en/using-matchers.html#content)
- [Enzyme Docs](https://enzymejs.github.io/enzyme/)

#### Process
- Add the test dependencies
- $ `yarn add -D enzyme react-test-renderer enzyme-adapter-react-16`
- $ `yarn test`
- Control + C to stop the testing suite

---
### Jest
When you create a new React application, we get Jest automatically, which is great because Enzyme must be used in conjunction with a testing suite like Jest. On top of Jest being bundled in with our application, it also creates a test file for App.js. It has one test that looks at React's boilerplate code.

### Enzyme
Enzyme uses Jest and layers on React specific functionality. Adding Enzyme makes working with React components even better, by allowing us to render a component or page for us and allow us to query the elements rendered.

Additionally, much like React's "hot-reload" when we run our React server, once we run $ `yarn test` it will continue to run and watch our file structure for any changes and re-run the test automatically for us.

### Organizing Your Tests
Each component in the Cat Tinder application needs a corresponding test file. The files can be named the same as the component file with a `.test.js` file extension.

In this case, we will create a test file called *Home.test.js* in the directory in `src/pages`.

After we create our test file, we need to import in the following lines at the top of our file:

**`src/pages/Home.test.js`**
```javascript
// Imports React into our test file.
import React from 'react'

// Imports Enzyme testing and deconstructs Shallow into our test file.
import Enzyme, { shallow } from 'enzyme'

// Imports Adapter utilizing the latest react version into our test file so we can run a testing render on any component we may need.
import Adapter from 'enzyme-adapter-react-16'

// Imports in the component we are going to be testing.
import Home from './Home'

//Allows us to utilize the adapter we import in earlier, allowing us to call and render a component.
Enzyme.configure({adapter: new Adapter()})
```

Let's write a test to check for the text rendering in our components. We will write a test, then we'll update the code to make it pass. (That's TDD!)

```javascript
describe("When Home renders", () => {
  it("displays a heading", () => {
    const home = shallow(<Home />)
    const homeHeading = home.find("h3").text()
    expect(homeHeading).toEqual("Welcome to Cat Tinder!")
  })
})
```
Notice we import `__shallow__` from Enzyme. Here we create a variable that utilizes shallow to instantiate an instance of our Home component. The magic of Enzyme is that once we have our component instanced, we can then call `home.find("h3").text()` to inspect the DOM of that component, find our paragraph element and look at the text it's wrapping.

There are a lot of different matchers out there. We can expect our component to contain elements, or be greater/lesser than something, to be true or to be false... etc.

Refer to the [Jest Matchers](https://facebook.github.io/jest/docs/en/using-matchers.html#content) docs for more information on what matchers to use and how to utilize them in your expects.

---
## Challenge: Cat Tinder Tests
- Add Enzyme to your application
- Add a test file for the Home, Header, Footer, and NotFound components with the `.test.js` extension.
- Create a test for each page, checking that the page is rendering by asserting against a single JSX element.


## Stretch Challenges
- As a developer, I can make my tests more DRY by declaring reusable variables in global scope.
- Create an additional test for the component `Home.js` that checks for the first `img` tag and all of its props.
- Create an additional test for the component `Header.js` that checks for a tag by its class name to contain some text.

---
[Back to Syllabus](../../README.md#cat-tinder-frontend)
