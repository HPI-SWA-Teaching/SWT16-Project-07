# AcceptIt 

Branch  | Travis CI  | Code Coverage |
------- | ---------- | ------------- |
master  | [![Build Status](https://travis-ci.org/hpi-swa-teaching/AcceptIt.svg?branch=master)](https://travis-ci.org/hpi-swa-teaching/AcceptIt) | |
develop | [![Build Status](https://travis-ci.org/hpi-swa-teaching/AcceptIt.svg?branch=develop)](https://travis-ci.org/hpi-swa-teaching/AcceptIt) | [![Coverage Status](http://coveralls.io/repos/github/hpi-swa-teaching/AcceptIt/badge.png?branch=develop)](https://coveralls.io/github/hpi-swa-teaching/AcceptIt) |

# Installation  

1. Make sure you have [metacello-work](https://github.com/dalehenrich/metacello-work) installed in your image.

2. Follow the following Guide for the [git repo setup](https://github.com/hpi-swa-teaching/AcceptIt/wiki/Git-setup-guide)
If you follow the guide there is no need for Step 3.

3. AcceptIt can be acquired by running following code in the workspace:

```smalltalk
Metacello new
  baseline: 'AcceptIt';
  repository: 'github://hpi-swa-teaching/AcceptIt/packages';
  get;
  load
```

# Usage

1. Choose a class to test like for example "MySuperCalculator" You can also use the ACReadMeFactory to execute exactly the here described steps.

2. Create a user story by running the following code in the workspace:  
```smalltalk
ACUserStory createUserStory:
'AC Calculator User Story
As a developer
I want to do basic calculus (add, subtract, multiply, devide)
In order to determine the result of some formula'
withCategory: 'acceptitTest-calculator'
```

3. Create a library like this:   
```smalltalk
ACLibrary 
	subclass: 'MySuperCalculatorTESTLibrary' asSymbol
	instanceVariableNames: ''
	classVariableNames: ''
	poolDictionaries: ''
	category: 'AcceptitGenerated'
``` 
4. Add a `libraries` method on class side to your user story class and make it return the class of it's library 

```
libraries

  ^ {MySuperCalculatorLibrary}

```

5. write the test scenario in your user story
```
minimalExampleUS

Given A is true
When I do nothing
Then I expect A to be true

6. Add needed methods to the library like
```smalltalk
(given) A is :aBool
  MySuperCalculatorLibrary a: aBool.
```
  
```smalltalk
(when) I do nothing

```
```smalltalk
(then) I expect A to be :aBool
	self assert: [MySuperCalculatorLibrary a = aBool].
```
7. Add the according methods on class side (also add an instance variable `a` on class side):
```smalltalk
a: aBool
  a := aBool.
```
```smalltalk
a
  ^a
```

8. Run the Test-Runner
```smalltalk
ACTestRunner open
```

Known Issues:
1. Currently acceptit doesn't work with squot/git, we are working on a fix.
