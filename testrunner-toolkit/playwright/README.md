# Jest with Playwright
This folder contains a simple set up for Jest and Playwright which can be run locally and with the Sauce Labs Testrunner Toolkit

## Local Usage
### Install dependencies
You can install all dependencies by running the following command

    npm install
    
This will install all needed dependencies that are listed in the `package.json`-file

> NOTE: Make sure you are in the folder `testrunner-toolkit/playwright` when you execute this command

### Run tests locally
You can run the tests on your local machine, the only thing you need to have is Chrome. If you have it you can run this command

    npm run test.local

It will run all tests in *headless*-mode, meaning you will not see a browser starting, but the logs will look like this

```log
➜  jest-playwright git:(feat/jest-playwright) ✗ npm run test.local
> jest-playwright-examples@1.0.0 test.local /jest-playwright
> jest --verbose

 PASS   browser: chromium  test/specs/login.spec.js
  LoginPage
    ✓ should be able to test loading of login page (510 ms)
    ✓ should be able to login with a standard user (973 ms)
    ✓ should not be able to login with a locked user (381 ms)

 PASS   browser: chromium  test/specs/cart.summary.spec.js
  Cart Summary page
    ✓ should validate that we can continue shopping (1323 ms)
    ✓ should validate that we can go from the cart to the checkout page (333 ms)
    ✓ should validate that a product can be removed from the cart (321 ms)

 PASS   browser: chromium  test/specs/checkout.summary.spec.js
  Checkout - Summary
    ✓ should validate that we can continue shopping (977 ms)
    ✓ should validate that we can cancel checkout and go to the inventory page (381 ms)
    ✓ should validate that we have 1 product in our checkout overview (338 ms)

 PASS   browser: chromium  test/specs/swag.item.details.spec.js
  Swag Item Details
    ✓ should validate that we can go back from the details to the inventory page (1585 ms)
    ✓ should validate that a product can be added to a cart (435 ms)
    ✓ should validate that a product can be removed from the cart (341 ms)

 PASS   browser: chromium  test/specs/swag.items.list.spec.js
  Swag items list
    ✓ should validate that all products are present (874 ms)
    ✓ should validate that the details of a product can be opened (844 ms)
    ✓ should validate that a product can be added to the cart (361 ms)
    ✓ should validate that a product can be removed from the cart (263 ms)
    ✓ should be able to open the cart summary page (251 ms)

 PASS   browser: chromium  test/specs/checkout.complete.spec.js
  Checkout - Complete
    ✓ should be able to test loading of login page (330 ms)

 PASS   browser: chromium  test/specs/checkout.personal.info.spec.js (6.355 s)
  Checkout - Personal info
    ✓ should validate we get an error if we don not provide all personal information (950 ms)
    ✓ should validate that we can cancel the first checkout (3164 ms)
    ✓ should be able to continue the checkout (167 ms)

 PASS   browser: chromium  test/specs/menu.spec.js (6.492 s)
  Menu
    ✓ should be able to the swag items overview page (1340 ms)
    ✓ should be able to open the about page (1453 ms)
    ✓ should be able to log out (997 ms)
    ✓ should be able to clear the cart (627 ms)

Test Suites: 8 passed, 8 total
Tests:       25 passed, 25 total
Snapshots:   0 total
Time:        7.912 s
Ran all test suites.
```

You can also run the test in *headfull*-mode with this command

    npm run test.local.headfull
    
You will then see Chrome poping up.

## Sauce Labs Testrunner Toolkit
### Install dependencies

Follow instructions from [here](https://github.com/saucelabs/testrunner-toolkit)

> NOTE: Make sure you are in the folder `testrunner-toolkit/playwright` when you execute this command

### Run tests in Sauce

    saucectl run

It will run all tests and the logs will look like this

```log
saucectl run

> sauce-playwright-runner@0.0.0 test /home/seluser
> DISPLAY="$(cat DISPLAY)" DEBUG="playwright:*" jest --config=./.config/jest.config.js --runInBand

Setting test timeout to 60sec

PASS tests/specs/swag.items.list.spec.js (7.546s)
Setting test timeout to 60sec

PASS tests/specs/swag.item.details.spec.js (5.647s)
Setting test timeout to 60sec

PASS tests/specs/cart.summary.spec.js
Setting test timeout to 60sec

PASS tests/specs/checkout.personal.info.spec.js (8.001s)
Setting test timeout to 60sec

PASS tests/specs/menu.spec.js (7.958s)
Setting test timeout to 60sec

PASS tests/specs/checkout.summary.spec.js
Setting test timeout to 60sec

PASS tests/specs/login.spec.js
Setting test timeout to 60sec

PASS tests/specs/checkout.complete.spec.js

Test Suites: 8 passed, 8 total
Tests:       25 passed, 25 total
Snapshots:   0 total
Time:        48.223s
Ran all test suites.

Open job details page: https://app.eu-central-1.saucelabs.com/tests/69d115d3f59d44a897581a0557ccd1ed

```
