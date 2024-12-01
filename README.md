# Auto Read Aloud on ChatGPT
userscript that automatically clicks "Read aloud" buttons on chatgpt.com  

Tested on 2024/11/30  
I'm using this script, bugfix will be quick but not guaranteed.  
Feel free to adjust/re-publish the script.

# How to install
1. Install [Tampermonkey](https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) 
1. Enable [Developer mode](https://www.tampermonkey.net/faq.php?locale=en#Q209)
1. Click this link [Install the script](https://raw.githubusercontent.com/iha-hiroa/Auto-Read-Aloud-on-ChatGPT-for-Edge/refs/heads/main/main.user.js)
2. Go https://chatgpt.com/
3. login to show "Read aloud" button

# How works
1. Every 1 second, check the element 'button[aria-label="Read aloud"]'
2. If find it, and it's not clicked before, click it.
```
(function() {
    'use strict';
    console.log(`Auto Read Aloud on ChatGPT for Edge: loaded`);

    // Initialize a Set to keep track of clicked button selectors
    const clickedButtons = new Set();

    // Function to find and click new buttons
    function checkAndClickButtons() {
        // console.log(`Auto Click Read Aloud on ChatGPT: Checking`);

        // Find all buttons with the specified aria-label
        const buttons = document.querySelectorAll('button[aria-label="Read aloud"]');

        buttons.forEach(button => {
            // Get the full selector for the button
            const selector = button;

            // Skip if the button was already clicked
            if (clickedButtons.has(selector)) return;

            // Click the button
            button.click();
            // console.log(`Auto Click Read Aloud on ChatGPT: Clicked`);

            // Remember the button as clicked
            clickedButtons.add(selector);
        });
    }

    // Run the check periodically
    const interval = 1000; // Check every 1 second
    setInterval(checkAndClickButtons, interval);
})();
```
