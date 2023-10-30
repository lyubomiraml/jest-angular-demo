## Setup jest in a new angular project

# Step 1 - Remove Karma related stuff:

	npm remove karma karma-chrome-launcher karma-coverage karma-jasmine karma-jasmine-html-reporter @types/jasmine jasmine-core


# Step 2 - Install @angular-builders/jest and jest:

	npm i @angular-builders/jest jest @types/jest jest-preset-angular --save-dev 

# Step 3 - Update your Typescript configurations:

	In tsconfig.spec.json (root directory or project roots, used by Jest):

		- Replace jasmine in types array with jest
		You want your tests to be type-checked against Jest typings and not Jasmine

# Step 4 - Create file jest.config.js file in the root directory

	module.exports = {
	preset: "jest-preset-angular",
	globalSetup: "jest-preset-angular/global-setup",
	roots: ["<rootDir>"],
	};

# Step 5 - Update test configuration in angular.json

	"test": {
		"builder": "@angular-builders/jest:run",
		"options": {
			"configPath": "jest.config.js",
			"globalMocks": []
		}
	}

# Step 6 - Run tests 
	ng test



## Run and debug a single test in Visual Studio Code
1. Select the `Run and Debug` page from the left navigation pane;
2. On the top drop-down menu select `Jest Current File` or `Jest Current File(watch)`;
3. Click on the Green play button next to the drop-down;
4. Using both approaches you can set breakpoints in your test and ng files;
