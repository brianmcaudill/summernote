
```markdown
## FAQ: Toolbar Customization in AirMode

**Q: Why isn't the toolbar property being used when I enable airMode in Summernote?**

A: This is actually expected behavior in Summernote. 

**TLDR:**
The toolbar property isn't used in airMode. To customize tools in airMode, use the `popover` option instead:

```javascript
$('#summernote').summernote({
  airMode: true,
  popover: {
    air: [
      ['style', ['style']],
      ['font', ['bold', 'italic', 'underline', 'clear']],
      ['para', ['ul', 'paragraph']],
      ['insert', ['link']]
    ]
  }
});
```
Here's a breakdown of the situation and some possible solutions:

1. **AirMode and Toolbar Incompatibility:**
   When airMode is enabled, Summernote provides a minimal, floating toolbar that appears when text is selected. In this mode, the regular toolbar is not used.

2. **Code Confirmation:**
   This behavior is confirmed in the `Toolbar.js` file:
   ```javascript
   shouldInitialize() {
     return !this.options.airMode;
   }
   ```
   This method prevents the regular toolbar from initializing when airMode is enabled.

3. **AirMode Behavior:**
   In airMode, Summernote creates a popover with a subset of editing options. This popover can't be fully customized like the regular toolbar.

4. **Possible Solutions:**
   a. For a custom toolbar with airMode-like functionality, disable airMode and create a custom floating toolbar using Summernote's API and custom CSS.
   
   b. To customize the airMode popover, use the `popover` option in Summernote's configuration:
   ```javascript
   $('#summernote').summernote({
     airMode: true,
     popover: {
       air: [
         ['style', ['style']],
         ['font', ['bold', 'italic', 'underline', 'clear']],
         ['para', ['ul', 'paragraph']],
         ['insert', ['link']]
       ]
     }
   });
   ```

5. **Contributing:**
   If you believe this limitation is significant, consider contributing to Summernote by proposing and implementing a feature for toolbar customization in airMode.

I understand your concern. Let's add this issue to our FAQ and provide a solution. I'll update the FAQ with a new entry addressing this problem:

```markdown
## FAQ: Toolbar Customization in AirMode

**Q: Why isn't the toolbar property being used when I enable airMode in Summernote?**

A: This is actually expected behavior in Summernote. 

**TLDR:**
The toolbar property isn't used in airMode. To customize tools in airMode, use the `popover` option instead:

```javascript
$('#summernote').summernote({
  airMode: true,
  popover: {
    air: [
      ['style', ['style']],
      ['font', ['bold', 'italic', 'underline', 'clear']],
      ['para', ['ul', 'paragraph']],
      ['insert', ['link']]
    ]
  }
});
```

[... previous content ...]

**Q: When I have multiple Summernote instances on the page in airMode, the popover doesn't close when I open another one or click away. How can I fix this?**

A: This is a known issue with Summernote in airMode. To resolve this, you can implement a custom solution to close other popovers when a new one is opened or when clicking outside. Here's an example of how to do this:

```javascript
$(document).ready(function() {
  // Initialize all Summernote instances
  $('.summernote').summernote({
    airMode: true,
    popover: {
      air: [
        ['style', ['style']],
        ['font', ['bold', 'italic', 'underline', 'clear']],
        ['para', ['ul', 'paragraph']],
        ['insert', ['link']]
      ]
    }
  });

  // Close all popovers when clicking outside
  $(document).on('click', function(e) {
    if (!$(e.target).closest('.note-editable, .note-popover').length) {
      $('.summernote').summernote('destroy');
      $('.summernote').summernote({
        airMode: true,
        popover: {
          air: [
            ['style', ['style']],
            ['font', ['bold', 'italic', 'underline', 'clear']],
            ['para', ['ul', 'paragraph']],
            ['insert', ['link']]
          ]
        }
      });
    }
  });

  // Close other popovers when opening a new one
  $('.summernote').on('summernote.focus', function() {
    $('.summernote').not(this).each(function() {
      $(this).summernote('destroy');
      $(this).summernote({
        airMode: true,
        popover: {
          air: [
            ['style', ['style']],
            ['font', ['bold', 'italic', 'underline', 'clear']],
            ['para', ['ul', 'paragraph']],
            ['insert', ['link']]
          ]
        }
      });
    });
  });
});
```

This solution does the following:
1. Initializes all Summernote instances with airMode.
2. Adds a click event listener to the document that closes all popovers when clicking outside of Summernote areas.
3. Adds a focus event listener to each Summernote instance that closes other popovers when a new one is opened.

Note that this solution involves destroying and reinitializing Summernote instances, which might not be ideal for performance if you have many instances on the page. In that case, you might need to explore more optimized solutions or consider contributing an enhancement to the Summernote project.
I understand your concern. Let's add this issue to our FAQ and provide a solution. I'll update the FAQ with a new entry addressing this problem:

```markdown
## FAQ: Toolbar Customization in AirMode

**Q: Why isn't the toolbar property being used when I enable airMode in Summernote?**

A: This is actually expected behavior in Summernote. 

**TLDR:**
The toolbar property isn't used in airMode. To customize tools in airMode, use the `popover` option instead:

```javascript
$('#summernote').summernote({
  airMode: true,
  popover: {
    air: [
      ['style', ['style']],
      ['font', ['bold', 'italic', 'underline', 'clear']],
      ['para', ['ul', 'paragraph']],
      ['insert', ['link']]
    ]
  }
});
```

[... previous content ...]

**Q: When I have multiple Summernote instances on the page in airMode, the popover doesn't close when I open another one or click away. How can I fix this?**

A: This is a known issue with Summernote in airMode. To resolve this, you can implement a custom solution to close other popovers when a new one is opened or when clicking outside. Here's an example of how to do this:

```javascript
$(document).ready(function() {
  // Initialize all Summernote instances
  $('.summernote').summernote({
    airMode: true,
    popover: {
      air: [
        ['style', ['style']],
        ['font', ['bold', 'italic', 'underline', 'clear']],
        ['para', ['ul', 'paragraph']],
        ['insert', ['link']]
      ]
    }
  });

  // Close all popovers when clicking outside
  $(document).on('click', function(e) {
    if (!$(e.target).closest('.note-editable, .note-popover').length) {
      $('.summernote').summernote('destroy');
      $('.summernote').summernote({
        airMode: true,
        popover: {
          air: [
            ['style', ['style']],
            ['font', ['bold', 'italic', 'underline', 'clear']],
            ['para', ['ul', 'paragraph']],
            ['insert', ['link']]
          ]
        }
      });
    }
  });

  // Close other popovers when opening a new one
  $('.summernote').on('summernote.focus', function() {
    $('.summernote').not(this).each(function() {
      $(this).summernote('destroy');
      $(this).summernote({
        airMode: true,
        popover: {
          air: [
            ['style', ['style']],
            ['font', ['bold', 'italic', 'underline', 'clear']],
            ['para', ['ul', 'paragraph']],
            ['insert', ['link']]
          ]
        }
      });
    });
  });
});
```

This solution does the following:
1. Initializes all Summernote instances with airMode.
2. Adds a click event listener to the document that closes all popovers when clicking outside of Summernote areas.
3. Adds a focus event listener to each Summernote instance that closes other popovers when a new one is opened.

Note that this solution involves destroying and reinitializing Summernote instances, which might not be ideal for performance if you have many instances on the page. In that case, you might need to explore more optimized solutions or consider contributing an enhancement to the Summernote project.
References (10)
1. 
USAGE.md - 0-63
2. 
airmode.html - 1-27
3. 
HintPopover.spec.js - 1-6
4. 
toolbar-container.html - 29-37
5. 
LinkDialog.spec.js - 1-6
6. 
AirPopover.js - 8-56
7. 
ondialog.html - 1-27
8. 
plugin-hello.html - 0-35
9. 
history-limit.html - 1-28
10. 
external-codemirror.html - 43-65

## FAQ: Image Pasting Issues

**Q: When I paste an image, Summernote creates two images instead of one. How can I fix this?**

A: This is not the expected behavior. The issue might be caused by conflicting event handlers or plugin interactions. Here are some steps to troubleshoot and resolve the issue:

1. **Check for conflicting event handlers:**
   Make sure you don't have multiple event handlers for the paste event. Look for any custom `paste` event handlers in your code.

2. **Disable and re-enable plugins:**
   If you're using any plugins, try disabling them one by one to isolate if a particular plugin is causing the issue.

3. **Update Summernote:**
   Ensure you're using the latest version of Summernote, as this issue might have been fixed in a recent update.

4. **Custom paste handling:**
   If the issue persists, you can try implementing a custom paste handler to ensure only one image is inserted. Here's an example:

   ```javascript
   $('#summernote').summernote({
     callbacks: {
       onPaste: function (e) {
         var bufferText = ((e.originalEvent || e).clipboardData || window.clipboardData).getData('Text');
         e.preventDefault();
         
         // Firefox fix
         setTimeout(function () {
           document.execCommand('insertText', false, bufferText);
         }, 10);
       }
     }
   });
   ```

5. **Check browser compatibility:**
   Test the behavior in different browsers to see if it's browser-specific.

If none of these solutions work, it would be helpful to create a minimal reproducible example and report it as an issue on the Summernote GitHub repository.
```

Now, let's dive deeper into troubleshooting this specific issue:

1. **Version Check**: First, make sure you're using the latest version of Summernote. Some bugs might have been fixed in recent updates.

2. **Isolation Test**: Try creating a minimal HTML file with just Summernote and test the image pasting there. This will help determine if the issue is with Summernote itself or caused by other parts of your application.

3. **Event Listener Inspection**: Use browser developer tools to inspect if there are multiple paste event listeners attached to the Summernote editor.

4. **Custom Paste Handler**: If the issue persists, you can try implementing a custom paste handler to ensure only one image is inserted. Here's an example:

```javascript
$('#summernote').summernote({
  callbacks: {
    onPaste: function (e) {
      var clipboardData = e.originalEvent.clipboardData;
      if (clipboardData && clipboardData.items && clipboardData.items.length) {
        var items = clipboardData.items;
        for (var i = 0; i < items.length; i++) {
          if (items[i].type.indexOf('image') !== -1) {
            var blob = items[i].getAsFile();
            var reader = new FileReader();
            reader.onload = function(event) {
              var base64data = event.target.result;
              $('#summernote').summernote('insertImage', base64data);
            };
            reader.readAsDataURL(blob);
            e.preventDefault();
            return;
          }
        }
      }
    }
  }
});
```

This custom handler will prevent the default paste behavior and manually insert the image, which should prevent duplication.

5. **Debugging**: If you're comfortable with debugging JavaScript, you could set a breakpoint in the Summernote source code where images are inserted and step through to see why it's happening twice.

6. **Report the Issue**: If you've tried these steps and the issue persists, it would be valuable to report this as a bug to the Summernote GitHub repository. Provide a minimal reproducible example, your Summernote version, and browser information.

**Making changes directly to the Summernote codebase to fix this issue**

1. First, we need to locate the relevant file in the Summernote source code. Based on the project structure, the image handling is likely in the `src/js/base/module/Editor.js` file.

2. In this file, we need to find the method that handles pasting. It's probably named something like `pasteByEvent` or `handlePasteEvent`.

3. Once we've found this method, we need to modify it to prevent duplicate image insertions. Here's a potential fix:

```javascript
handlePasteEvent(event) {
  const clipboardData = event.clipboardData || window.clipboardData;
  const pastedData = clipboardData.getData('text');
  const imageInserted = false;

// Check if pasted content contains images
if (clipboardData && clipboardData.items && clipboardData.items.length) {
  const items = clipboardData.items;
  for (let i = 0; i < items.length; i++) {
    if (items[i].type.indexOf('image') !== -1) {
      const blob = items[i].getAsFile();
      const reader = new FileReader();
      reader.onload = (e) => {
        const base64data = e.target.result;
        this.insertImage(base64data);
      };
      reader.readAsDataURL(blob);
      event.preventDefault();
    }
  }
}

  // If no image was inserted, proceed with default paste behavior
  if (!imageInserted) {
    // Existing paste logic here...
  }
}
```
  References (3)
  1. USAGE.md - 376-376
  2. Editor.spec.js - 109-115
  3. Editor.spec.js - 108-116

4. After making these changes, you'll need to rebuild the Summernote project. This typically involves running a build script, which might be something like:

```
npm run build
```

5. Test the changes thoroughly to ensure they solve the problem without introducing new issues.

6. If the changes work as expected, you should commit these changes and create a pull request to the Summernote repository on GitHub.

Remember, this is a suggested fix and might need adjustments based on the exact structure of the Summernote codebase. Also, it's a good practice to add comments explaining the changes and maybe even add a test case for this scenario.

If you need help with any specific part of this process, or if you encounter any issues while implementing these changes, please let me know and I'll be happy to assist further.

How can I ensure that the Summernote editor is secure against code injection attacks?
Tabnine
Claude 3.5 Sonnet
To ensure that the Summernote editor is secure against code injection attacks, you should implement the following measures:

1.
Use the built-in XSS filter:
Summernote has a built-in XSS filter that you can enable in the configuration:

$('#summernote').summernote({
  callbacks: {
    onInit: function() {
      $('body').on('submit', 'form', function() {
        $(this).find('.summernote').each(function() {
          $(this).val($(this).summernote('code'));
        });
      });
    }
  },
  codeviewFilter: true,
  codeviewIframeFilter: true
});
Insert
Copy

2.
Sanitize the HTML on the server-side:
Even with client-side filtering, always sanitize the HTML on the server-side before storing or displaying it. Use a robust HTML sanitization library appropriate for your server-side language.
3.
Limit allowed tags and attributes:
Configure Summernote to only allow specific HTML tags and attributes:

$('#summernote').summernote({
  sanitizeHtml: true,
  allowedTags: ['p', 'br', 'strong', 'em', 'ul', 'ol', 'li', 'a'],
  allowedAttributes: {
    'a': ['href', 'target']
  }
});
Insert
Copy

4.
Disable certain features:
If you don't need certain potentially risky features, disable them:

$('#summernote').summernote({
  disableDragAndDrop: true,
  codeview: false
});
Insert
Copy

Remember, client-side security measures can be bypassed, so always implement server-side sanitization as well.
References (6)
1. 
hint-userdefine.html - 45-49
2. 
codemirror.html - 42-46
3. 
hint-words.html - 65-68
4. 
hint-math.html - 51-54
5. 
external-codemirror.html - 43-65
6. 
hint-words.html - 1-63