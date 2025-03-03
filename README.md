# Star Wars Planets API - Testing with Stubs

This project demonstrates how to use **stubs** with the `sinon` library to test API requests without making actual calls to the **Star Wars API (SWAPI)**. The implementation includes:
- A service for fetching planet data from SWAPI.
- Tests using `sinon.stub` to mock API responses.
- Usage of `assert` for validation.

## Why Use Stubs?

Stubs are a type of test double that replace a function and return controlled outputs. This is particularly useful when:

- You want to **avoid calling external APIs** to reduce test time and prevent rate limits.
- You need to test different responses without relying on real API data.
- You want your tests to be **fast, deterministic, and independent** of network conditions.

## 🛠 Technologies Used
- **Node.js**
- **Sinon.js** (for stubbing API calls)
- **Assert** (for test assertions)

## 📁 Project Structure
```
📂 javascript-expert--stubs
 ┣ 📂 mocks
 ┃ ┣ 📝 alderaan.json  # Mock response for Alderaan
 ┃ ┣ 📝 tatooine.json  # Mock response for Tatooine
 ┣ 📂 src
 ┃ ┣ 📝 service.js  # Service handling API requests
 ┃ ┣ 📝 service.test.js  # Test file with stubs
 ┣ 📝 README.md  # Project documentation
 ┣ 📝 package.json  # Dependencies and scripts
```

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/willyoliv/javascript-expert--stubs.git
   cd javascript-expert--stubs
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

## Running Tests

To run tests, use the following command:
```sh
npm test
```
This will execute `service.test.js`, which includes test cases using stubs.

## 📌 How It Works
### `service.js`
- Defines the `Service` class with `makeRequest` (fetches data from API) and `getPlanets` (processes the data).

### `service.test.js`
- Uses `sinon.stub()` to mock API responses.
- Prevents unnecessary network calls by returning predefined responses from `mocks/alderaan.json` and `mocks/tatooine.json`.
- Uses `assert.deepStrictEqual()` to verify the expected output.

## 📝 Example of a Stubbed Test
```javascript
const service = new Service();
const stub = sinon.stub(service, service.makeRequest.name);

stub.withArgs(BASE_URL_1).resolves(mocks.tatooine);
stub.withArgs(BASE_URL_2).resolves(mocks.alderaan);

const result = await service.getPlanets(BASE_URL_1);
assert.deepStrictEqual(result, {
  name: 'Tatooine',
  surfaceWater: '1',
  appearedIn: 5
});
```

## 📖 Learn More
- [Sinon.js Documentation](https://sinonjs.org/)
- [Star Wars API (SWAPI)](https://swapi.dev/)

---





