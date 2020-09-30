# QA Engineering Assessment

## Intro
The goal of this assessment is to test a simplistic web app, note any bugs, and document how to reproduce them. Open the index.html page in google chrome for this test. The page will load a script called bundle.min.js, which is intentionally obfuscated. Use the questions below as a guide to what to include in your analysis. Reach out to the hiring manager with any questions.

### Questions
* Describe what bundle.min.js is doing to the page, and try to determine what would happen if the script were not present.
    * bundle.min.js is displaying the content of this webpage . Without the script, there would be no content (no button, no text, etc).
* The button triggers a network request. Review these requests and note any inconsistencies if any. Look for anything notable in the console output
    * Whenever the button triggers a network request for 'https://reqres.in/api/colors/0, it runs into a 404 error, which is displayed in the console.
* Does the interface function as described?
    * No. The interface fails when randomly hitting the 'https://reqres.in/api/colors/0' api endpoint. In addition, when the page is refreshed, the previous color is not remembered, but the color before the last one.
* Are there any missing validation rules the code should be following?
* How are styles being applied to the elements on the page?
    * The css of the the page is being change for the <body> element to different 'rgb' values for the background-color property.
* Document any steps necessary to reproduce bugs. Include any steps needed to reset the app to its initial state.
* Are there any suggested changes to the code based on the behavior of the script?
