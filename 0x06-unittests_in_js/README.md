# Unittests in Javascript
Unit testing in JavaScript is the process of testing individual units of your code—like functions or methods—in isolation to ensure they work as expected. Unit tests are typically automated and written using testing libraries or frameworks like **Jest**, **Mocha**, or **Jasmine**.

Here’s a breakdown of what i have learnt and implemented in this repo:

---

## **Key Concepts in Unit Testing**
1. **Test Cases**: A single unit of testing logic, designed to verify that a specific function behaves as expected.
2. **Test Suites**: A group of related test cases.
3. **Assertions**: Statements that check if a given condition is true.
4. **Mocking**: Replacing dependencies or functions with mock versions to test units in isolation.
5. **Setup and Teardown**: Code that runs before (setup) or after (teardown) a test or suite, used for preparing the test environment.

---

## **Getting Started**
### 1. **Choose a Testing Framework**
Popular JavaScript testing frameworks include:
- **[Jest](https://jestjs.io/)**: A comprehensive framework with built-in assertions, mocking, and coverage tools.
- **[Mocha](https://mochajs.org/)**: A flexible testing framework, often paired with assertion libraries like Chai.
- **[Jasmine](https://jasmine.github.io/)**: A BDD-focused testing library.
- **[QUnit](https://qunitjs.com/)**: A simple framework, ideal for testing in a browser.

### 2. **Set Up the Framework**
- Install a testing framework using `npm` or `yarn`:
  ```bash
  npm install --save-dev jest
  ```

- Create a test script in your `package.json`:
  ```json
  {
    "scripts": {
      "test": "jest"
    }
  }
  ```

---

## **Writing a Simple Unit Test**
Here’s a basic example using **Jest**:

### Example Code
Suppose you have a function that adds two numbers:
```javascript
// math.js
function add(a, b) {
  return a + b;
}

module.exports = add;
```

### Writing the Test
```javascript
// math.test.js
const add = require('./math');

test('adds 1 + 2 to equal 3', () => {
  expect(add(1, 2)).toBe(3);
});
```

### Run the Test
- Run the test script:
  ```bash
  npm test
  ```

---

## **Advanced Topics**
1. **Testing Asynchronous Code**
   ```javascript
   // asyncFunction.js
   async function fetchData() {
     return 'Hello, World!';
   }

   module.exports = fetchData;

   // asyncFunction.test.js
   const fetchData = require('./asyncFunction');

   test('fetches data successfully', async () => {
     const data = await fetchData();
     expect(data).toBe('Hello, World!');
   });
   ```

2. **Mocking**
   - Jest makes mocking straightforward:
     ```javascript
     const fetchData = jest.fn(() => Promise.resolve('Mocked Data'));

     test('mocked function returns expected value', async () => {
       const data = await fetchData();
       expect(data).toBe('Mocked Data');
     });
     ```

3. **Code Coverage**
   - Jest includes a built-in coverage tool:
     ```bash
     npm test -- --coverage
     ```

4. **Setup and Teardown**
   ```javascript
   beforeEach(() => {
     // Code to run before each test
   });

   afterEach(() => {
     // Code to clean up after each test
   });
   ```

---

## **Best Practices**
- Keep your tests independent of each other.
- Aim for a high level of coverage (but remember, 100% coverage doesn’t always mean 100% tested).
- Use meaningful names for your test cases.
- Test both positive and negative scenarios.

---

### Resources
- Jest Documentation: [https://jestjs.io/docs](https://jestjs.io/docs)
- Mocha Documentation: [https://mochajs.org/](https://mochajs.org/)
- Jasmine Documentation: [https://jasmine.github.io/](https://jasmine.github.io/)