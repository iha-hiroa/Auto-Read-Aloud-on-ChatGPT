# Auto Read Aloud on ChatGPT for Edge
userscript that automatically clicks "Read aloud" buttons on chatgpt.com  

Only works on Edge  
Tested on 2024/11/30  
I'm using this script, bugfix will be quick but not guaranteed.  
Feel free to adjust/re-publish the script.

# How to install
1. Install [Edge](https://www.microsoft.com/en-us/edge/download) 
1. Install [Tampermonkey](https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd) on Edge 
1. Enable [Developer mode](https://learn.microsoft.com/en-us/microsoft-edge/extensions-chromium/getting-started/extension-sideloading) on Edge
1. Click this link [Install the script](https://raw.githubusercontent.com/iha-hiroa/Auto-Read-Aloud-on-ChatGPT-for-Edge/refs/heads/main/main.user.js)

# Quick view
You can copy and paste to your console.  
1. Open Edge
2. Go chatgpt.com
3. Press F12
4. Go console
5. Paste the code
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
