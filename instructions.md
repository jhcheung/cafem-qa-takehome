# QA Engineering Assessment

## Intro
The goal of this assessment is to test a simplistic web app, note any bugs, and document how to reproduce them. Open the index.html page in google chrome for this test. The page will load a script called bundle.min.js, which is intentionally obfuscated. Use the questions below as a guide to what to include in your analysis. Reach out to the hiring manager with any questions.

### Questions
* Describe what bundle.min.js is doing to the page, and try to determine what would happen if the script were not present.
    * bundle.min.js is displaying the content of the webpage/webapp. Without the script, there would be no content (no button, no text, etc), just a bunch of divs and potentially a background color based on the other script in the html.
* The button triggers a network request. Review these requests and note any inconsistencies if any. Look for anything notable in the console output
    * The primary inconsistency is that whenever the button triggers a network request for 'https://reqres.in/api/colors/0, it runs into a 404 error, which is displayed in the console and in the network tab.
* Does the interface function as described?
    * No. The interface fails when randomly hitting the 'https://reqres.in/api/colors/0' api endpoint. In addition, when the page is refreshed, the previous color is not remembered. Instead the color before the last is retained/remembered.
* Are there any missing validation rules the code should be following?
    * The 'https://reqres.in/api/colors/0' endpoint should be validated before displaying the new color line. In other words, the new color line is populated before it is verified that the color has been changed from hitting the API endpoint.
    * To resolve this, code should used to to validate the response of hitting the API endpoint and display an error if the response fails.
    * Alternatively, the code can just hit the endpoints ranged from 1-10 instead of 0-9
* How are styles being applied to the elements on the page?
    * The css of the the page is being changed for the <body> element to different 'rgb' values for the appropriate background-color property.
    * This changes each time the 'Get button' button is pressed.
* Document any steps necessary to reproduce bugs. Include any steps needed to reset the app to its initial state.
    * To reset the web app, open the web console in the browser and type in 'localStorage.clear()'. Then, refresh the page.
    * To test the network bug, first open the web debug console to the network tab or console tab.
        * Then, click the 'Get Color' button on the web app while keeping an eye out on the network tab or console tab. 
        * Continue clicking the 'Get Color' button until there is an error in the network or console tab when trying to acccess 'https://reqres.in/api/colors/0'
    * To test the saved color bug, first click the 'Get Color' button, and continue clicking until you get two consecutive different colors. Remember the colors
        * Please also make sure both 'Get Color' button presses are registered and did not fail due to the network bug.
        * Then, refresh the page and check what color the page background is. It should be the first of the two colors.
* Are there any suggested changes to the code based on the behavior of the script?
    * The 'https://reqres.in/api/colors/0' should not be used. Instead, the endpoints should range from 1-10.
    * Code should be written to validate the API call, to verify that the response from the API is good and to display an error if it is not.
    * The localStorage setting should be saved after the color is changed instead of before.
