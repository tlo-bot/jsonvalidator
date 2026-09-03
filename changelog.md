# Changelog

## v13

### 5/22/2026
**[Validator tab]**
- Bug fix for mixed arrays (Dariusz):
  - Change the schema generation function to generate schemas describing both primitive and object data types.
  - Change the template generation function to generate JSON template for all data types in `anyOf` rather than just the first.

### 5/15/2026
**[Validator tab]**
- Add runaway error protections
- Add click animations to purple buttons
- Pillbox tab style

### 5/14/2026
**[Validator tab]**
- Bug fix: when checking for duplicate keys in JSON Input field – unterminated strings could cause an infinite loop (Max)

### 5/13/2026
**[Validator tab]**
- Modified Schema generation for heterogenous arrays: the required fields in the schema will only contain keys that appear in every object in the array
- Bugs when Validating JSON against Schema fixed (Reynaldo):
  - Validation function previously flagged when any keys that were not present in Schema "required" was an error (though those keys should be optional but allowed)
  - Validation function did not work when Schema "type" was an array
- UX Change: added bar in Validation Results to display the validation against Schema which changes to a warning if the Input or Schema are edited
- Status indicator for Validation Results changes color depending on if there are any errors in the syntax validation or validation against Schema

### 5/12/2026
**[Validator tab]**
- Add 'Validate JSON against Schema' button which checks current JSON Input against current JSON Schema (Reynaldo)
- Bug when Generating Schema for Arrays fixed: for non-object items and objects with different types that are nested in arrays such as: `["cat",1]`, `[{"cat": "orange"},{"cat": 1}]`, the Generate Schema function now accommodates multiple types instead of only describing the last listed type (Dariusz)
- Validation results section now displays Warning for duplicate keys in an object (Dariusz)
- Small UI changes

### 05/11/2026
**[Validator tab]**
- Add a 'Reset' button to the JSON Input field which resets the field to the default JSON template (Dana)
- Modify the JSON template to reduce extra text, and add an array of objects (Dana)

### 04/14/2026
**[Validator tab]** Preserve trailing decimal zeros when prettifying & minifying in JSON Input field (Reynaldo)

### 04/13/2026
**[Validator tab]** Fixed bug where Ctrl+Z was undoing more in type history than just the wrapping. Now, Ctrl+Z after a wrapping action should only undo the wrapping action. (Reynaldo)

### 04/10/2026
**[Validator tab]**
- When there is a number in the Input field with trailing decimal zeros, have the corresponding schema-generated-type be `number` (though technically an integer), as number-type is more representative of the general data type
- Auto-close curly brackets, square brackets, and double quotes when typing in JSON Input field. Add wrapping feature where if a value is highlighted then `{`, `[`, or `"` is typed, the value will be wrapped with the opening and closing `{}`, `[]`, or `""`; the wrapping can be undone using Ctrl+Z. However, when the entire field is selected, the wrapping function will not take effect (in the case where the user uses Ctrl+A then types `{`, `[`, `"` to start writing a new JSON)
- Add auto-indentation for new lines in the JSON Input field which matches the indentation of previous lines

### 04/01/2026
**[Validator tab]** Included Add Descriptions button in the JSON Schema section which injects `"description": ""` for each property in the JSON Schema, with a toast message warning feature added to the JSON Schema Copy button that flags when a schema with an empty description is copied

### 03/16/2026
**[Diff tab]** For structural diffs (nested objects/arrays/fields): after clicking 'Examine in Diff tab' button, in the Diff tab there are 'Scroll to' buttons which scroll JSON 1 and JSON 2 to the lines that correspond to their respective values (Carina)

### 03/13/2026
**[Verifier/Diff tab]** Implemented structural diff: for nested objects/arrays/fields, flag top-level differences and attempt to match nested objects based on their key:value pairs, then compare those and flag their differences. If applicable, this structural diff will appear instead of the default line-diff. (Max)

### 03/09/2026
**[Verifier tab]** UI updates: "Go to line" → "Go to section", visual lines highlight flash when scrolling to section

### 03/06/2026
*See the second Verifier demo video.*
- **[Verifier tab]** Add dropdowns to Validation results sections which flag differences between actual and expected values (objects, arrays, strings, null values) when encountering `"result": false`. *(This was a great idea from discussion by all members of the testing group.)*
  - Each dropdown has a 'Go to line' button which scrolls the Verifier log to the relevant object with `"results": false` and also scrolls the page up to view the line
  - Each dropdown also has an 'Examine in Diff tab' button which will take the expected and actual values, then input them as JSON 1 and JSON 2 (respectively) in the Diff tab and automatically run the comparison. Clicking back to the Verifier tab will keep the y-scroll position (Sean)
- **[Diff tab]** Fix bug flagged by Max where JSON 2 code container lines weren't being properly highlighted
- Added functionality to all code containers to replace any non-breaking spaces (breaks JSON parsing) to regular spaces (Carina)
- Rescale main site container to the entire page

## v12_1

### 03/05/2026
- **[Verifier tab]** Change verifier tab regex search term `"score"` to `"score" : 0` so that `"score": 1` is not highlighted but `"score": 0` and `"score": 0.XX` etc. is
- **[Verifier tab]** Add verifier tab success search term `"score" : 1` flagged with green highlight (Max)
- **[Validator tab]** Add additional jsonschema validation to be closer to validation by PP by checking validity of keys. In particular, Adrian reported a bug where `"choices"` was used instead of `"enum"` and it was not flagged as invalid jsonschema by the tool (somewhat expected as this only had light schema validation)
- Fixed bug with text areas on all tabs where the line number height wasn't matching the text area height causing occasional mismatch between lines and line numbers

## v12

- **02/24/2026:** [Diff tab] Fixed bug raised by Reynaldo where objects with different key orders were being flagged as different
- **02/23/2026:** [Verifier tab] Added Ctrl+Enter functionality to 'Analyze Verifier' button
- **02/13/2026:** Added Verifier tab as suggested by Max which highlights relevant phrases that appear when the verifier marks `all_passed=false` and collapses all other sections

## v11

### 02/10/2026
- Added Diff tab (Sean & Reynaldo)
  - Changes the page to be more symmetrical for 2 JSON Input fields
  - Toggle to ignore order for arrays (Reynaldo & Sean)
  - Display the diff and also highlight the lines where there are differences (Carina)
  - Include escape/unescape functionality since verifier metadata on Circuit is typically escaped (Sean)
- Added 'Minimal' fake data toggle (Reynaldo, Carina, Max)
  - Instead of prepopulated fake data, replace with empty values and 0 as number to make editing quicker for gym task
- Added light schema validation (Max)
  - This will flag when prompt jsonschemas have issues and be double-validating with People Planner's "jsonschema" validation

## v10

### 01/27/2026
- Add schema generation-from-json data functionality (similar to the jsonv3 bookmarklet)
- Add fake json data-from-schema functionality to reduce/eliminate the use of Diya & possible errors from hallucinations (Max)
- Remove color legend and example buttons
- Clean up UI

## v7_2

### 01/26/2026
- Automatically copy minified JSON when using Copy button
