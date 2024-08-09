# Summernote Issues and Analysis

## 1. Bolding breaks with font-weight CSS rules applied
The fontStyling function in the Editor module needs review. Adjust CSS application logic for better handling of font-weight.

## 2. Summernote 0.8.20 and jQuery 4.0.0 Beta compatibility issues
Update core.js to ensure compatibility with newer jQuery versions. Test thoroughly with jQuery 4.0.0 Beta.

## 3. XSS Discovered in The Code View Function - Version 0.8.18+
Conduct a security audit of the Codeview module. Implement robust sanitization techniques for user input.

## 4. Summernote Editor unable to add editor area to an iframe
Enhance the initialization process in core.js to better support iframe integration. Consider adding specific iframe support.

## 5. Bullets & numbering doesn't work for copy-pasted content
Improve the Clipboard module's pasteHTML function to better preserve and handle list structures during paste operations.

## 6. Code paste for embed codes not working after fixing youtu.be links
Review recent changes in the Clipboard module. Adjust paste handling to properly manage various content types, including embed codes.

## 7. XSS Vulnerability Report: Discovering XSS Vulnerability through Data Schema Manipulation
Conduct a comprehensive security audit across all modules, with special attention to the Editor and Clipboard modules for data handling.

## 8. Insert Link modal - check symbol doesn't appear when clicking on "Open in new window" checkbox (ver 0.8.18)
Investigate the LinkDialog module's UI rendering logic, focusing on checkbox state management and visual feedback.

## 9. Disabled Ctrl+V Image base 64
Review the Clipboard module for any recent changes affecting image pasting. Update documentation if this is an intentional feature change.

## 10. Font Names dropdown getting reset
Examine the Buttons module's font selection persistence. Implement a more robust state management for font selections.

## 11. Line Height dropdown not adding checkmark to whole numbers
Review the Buttons module's line height functionality, focusing on UI state management for selected values.

## 12. Unable to insert image when clicking on picture button in Summernote
Examine the ImageDialog module's initialization and event handling. Ensure proper triggering of image insertion dialogs.

## 13. youtu.be URL does not work, though it worked in an older version (0.8.10)
Update the VideoDialog module to support current YouTube URL formats, including youtu.be links.

## 14. Not working with jQuery dialog
Adjust how Summernote initializes within jQuery UI dialogs, possibly in the core.js file. Ensure compatibility with jQuery UI components.

## 15. Issues in IE9 compatible browser from 0.8.18 to latest
Update env.js to improve support for older browsers like IE9. Consider polyfills or fallbacks for modern features.

## 16. Paste adds empty lines at the beginning and the end
Modify the Clipboard module's pasteByEvent function to trim unnecessary whitespace from pasted content.

## 17. Triple click selection applies styles to content below when applying ul/ol or paragraph alignments
Refine the Editor module's range handling for list and alignment operations, especially for multi-line selections.

## 18. Release ol/ul issue
Review and update list creation and manipulation logic in lists.js utility functions.

## 19. Cannot apply font size when selecting all (Ctrl+A)
Update the Editor module's font size application logic to handle full-document selections correctly.

## 20. Request to release v0.8.21
This is a project management task. Prepare for release by addressing critical bugs and updating documentation.

## 21. range.js:194 addRange(): The given range isn't in the document when calling 'insertImage'
Update the Editor module's image insertion logic to handle cases where the range is outside the document.

## 22. Initializing font size and line height at the same time causes issues
Adjust the Buttons module's initialization process for font size and line height to prevent conflicts.

## 23. Does not work properly with Bootstrap 5.2.3 and jQuery 3.7.1
Update core.js to ensure compatibility with newer versions of Bootstrap and jQuery. Test thoroughly with these versions.

## 24. Selection is lost on iOS devices when trying to change the selected text's font size
Improve mobile-specific handling in the Editor module, particularly for iOS devices and text selection persistence.

## 25. Discussion: v0.9.0 and further developments
This is a project planning task. Outline new features, improvements, and breaking changes for the next major version.

## 26. Do we still need emptyPara for focusing caret?
Reevaluate the Editor module's caret positioning logic. Consider alternative methods for maintaining focus.

## 27. IndexSizeError in Chrome: Still Occurring
Conduct a thorough review of the Editor module's range handling, particularly focusing on Chrome-specific issues.
