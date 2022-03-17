# Peroy Nel Aluminati Technical Assesment Submission:

To start working on the project I navigated to the github repository that was provided to me and I had a look at the ReadMe to gain some insight as to what the expectations are for me to complete.

I then made sure to download the repository in a Zip file and upon completion I extracted the project folder onto my desktop to begin working on it. 

In order to work with the project files I started up Visual Studio Code as my IDE of choice for this type of work. I then make sure that I open the working folder inside of Visual Studio Code, following this I make sure to open a new Terminal window through which I can verify that I have navigated to the project folder.

If I am indeed in my root directory I can continue by running the “npm install” command, this will then have a look at the package dependencies for the project and install all of the necessary modules.

When I had a look at the package.json file I could determine that I would be working with vue “^2.5.2” and as such I would refine my solutions around this version of vue.

# App.vue

I have made changes to the input number limits, setting the min value to 1 and the max value to 100. This is to keep in accordance with the specifications.
I made sure to change the v-model to v-model.number, this ensures that the results that we get are returned as typeof(Number) === true.
I implemented a computed method that listens for, updates and returns the limit change from 100 when it is modified in the input field by the user.
I passed the ‘number’ property to the ‘Numbers’ component, this allows me to pass through the value that I was returned from the getLimit computed method. This allows me to remove the watch method from Numbers.vue as this way the computed method is passing reactive data from the parent to the child instead of waiting for changes to be made before updating by letting the watch method listen to the parent for updates. This is a less taxing solution on the Vue engine and gives opportunity for scaling in real world applications.

# Numbers.vue

I renamed the method n() to listOfRandomNumbers() as n() is not a good choice of method name as it is not descriptive and would surely cause confusion to anyone who did not write the code by themselves but had to contribute to the project.
I added the props option and validated its type so that it returns the expected type of Number.
I removed the watch option from the code due to the fact that we are receiving the ‘number’ property that is set up to automatically return the input value from the parent component.
In the ‘listOfRandomNumbers()’ method I updated the variables so that ‘i = 1’ as this would ensure that that count starts at 1 and not 0 as per the specifications.
I updated 'i < this.limit' to 'i < (this.$prop.number)' as it will render a list of 1-100 instead of 1-99 as the previous solution had done.
Due to the limitations with the Math.random function in ‘listOfRandomNumbers()’ having a bias of only 0.5 I relied upon a well known ‘for loop’ randomisation algorithm called the “Fisher-Yates Shuffle”. This algorithm allows us to shuffle or randomise an array of values.
I updated the ‘nums’ constant to ‘this.$refs.numberRef so that the Vue Virual DOM $refs is used instead of the this.window DOM method that relies on document queries or selectors.
Changed ‘textContent’ to ‘innerText’ in the ‘num’ constant so that I get accurate values for each number.
I renamed the ‘hov’ method to ‘highlight’ so that it is more descriptive and in accordance with good coding practices.

# Spec
Using Vue, display all numbers from 1 to 100 in a random order on the screen. This number should be configurable via a provided input box.
If the user places their pointer over a given number, highlight that numbers' divisors.
For example, if the user hovers over 21, the numbers 1, 3, 7 would be highlighted. 22 would highlight 1, 2 and 11.

# Interview Task
The provided code is functional, but it's got some issues that need to be resolved. These issues may or may not be logical in nature - just because the code is working doesn't necessarily mean it is the best way of doing something.

Improve the code how you see fit - please leave comments to justify your decisions.

# GitHub Pull Requests
This is an interview task sent to prospective candidates to work at Aluminati. As such, all pull requests will be rejected. This code is, by its very nature, purposely designed with issues that candiates are asked to review!

If you have been invited to perform this test your submission should be through your point of contact with us, e.g. your recruitment agency.
