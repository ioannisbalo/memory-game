# Memory Game

## Description
A very simple, browser based, memory game.

## Getting Started

### Cloning the repository
This repository includes two submodules, one for the front-end and one for the back-end of the application.
To clone all the necessary components run: `git clone --recursive https://github.com/ioannisbalo/memory-game.git`

### Running the application
There are two available options to run the application, with docker and without.
If you have docker and docker-compose installed, I recommend you pick the first one.

* With Docker, simply run `yarn run docker` or `npm run docker`.
* Without Docker:
  1. Run `cd api; yarn install` and `cd ui; yarn install` from the root of the repository.
  2. Open two terminals and run `yarn run start-api` and `yarn run start-ui` respectively. Substitute with `npm` if needed.

Within a few seconds the application should be running. Navigate to `localhost:3000` to see the ui.

### Solution Architecture
Memory Game is a simple single-page application. That's why the client-server model was chosen.
This way, a clear seperation between game logic and data handling is achieved.
The front-end handles the game logic and the ui while the back-end provides the necessary data.

#### Game components:
* Game mode: The amount of cards the player needs to reveal in order. The choices are configurable by modifying the ui/src/Config.js.
* Random numbers: The values of the cards are generated in the back-end. The front-end queries by game mode and receives one sorted and one randomised list of numbers.
* Timer: Timing the elapsed time between the moment the player clicks "Start Guessing" and the moment they win. Implemented on the front-end.
* Leaderboard: Keeps track of the top five times per mode. Handled completely by the back-end.

### Libraries used
#### General
* `docker`: to make sure the application is running regardless of the system

#### Front-end
* `react`: it is one of the fastest ways to get a single-page application running
* `semantic-ui-react`: provides out-of-the-box styles which are useful given the time constraints

#### Back-end
* `nestjs`: it is, in my opinion, the cleanest back-end framework for nodejs, also uses Typescript which is a big bonus
* `class-validator`: useful for validation api input

### Possible improvements
* Authentication or calculation of scores on the back-end since now it's trivial to get on top of the leaderboard by sending a POST directly.
* More front-end unit testing.
* Animations for card turning.
* Production builds (currently using development builds everywhere).
* Nicknames/usernames associated with scores.
* Persistent data storage with a lightweight database or key-value store (Redis, leveldb, sqlite)
