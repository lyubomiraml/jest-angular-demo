## Setup jest in new angular project

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