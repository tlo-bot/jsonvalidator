# JSON Syntax Validator Tool

**Tool owner:** Teresa Lo

**Supported by:** Max Shengelia, Carina Yuen, Sean Sponagle, Reynaldo Guedes, Blake Tran, Jacques Core, Dana Tokatlian, and Dariusz Klimas

**Version:** v13

**Script link:** [https://github.com/tlo-bot/jsonvalidator/blob/main/jsonvalidatorv13.html] *(last updated: 06/01/2026)*

## Overview

The JSON Syntax validator is a toolkit with several functions:

### Validator

Used to check if JSON and JSON Schemas are valid, editing JSON, generating JSON templates from a JSON Schema, and generating JSON Schema from JSON.

- **JSON Input text field**
  - Dynamic validation of JSON shown by the Validation Results, which will highlight possible errors
  - **Copy:** copies minified JSON
  - **Prettify:** Expands JSON to readable format
  - **Minify:** Compacts JSON by removing newlines and spaces
  - **Generate Schema:** Generate corresponding JSON Schema based on the current JSON Input field & automatically copy the generated schema to clipboard in minified form
- **JSON Schema text field**
  - Dynamic validation of JSON Schema
  - **Template:** Generate a JSON template with "fake" data based on the current JSON Schema field
    - **Minimal toggle** (default = on): toggle between 'Minimal' fake data and placeholder data. Minimal data has empty strings, 0 for numbers, and true for booleans.
  - **Add Descriptions:** adds `"description": ""` for each property field in the schema
  - **Copy:** copies minified JSON Schema; shows warning if the schema being copied has empty description field(s)

### Verifier

Highlight key error phrases from verifier logs and collapse all other sections.

- **Analyze Verifier** (or press `Ctrl+Enter`): Analyze the verifier evalresults log to highlight relevant phrases that appear when the verifier marks `all_passed=false` and collapse all other sections
- Use carets next to line numbers to manually expand/collapse sections
- For more complicated JSON structure, use the **'Go to section'** and **'Examine in Diff tab'** buttons in the Validation Results to look more closely at the JSON
  - Nested arrays/objects have structural differences which groups objects based on similar key:value pairs and flags associated differences

### Diff

Find differences between two JSONs.

- **Copy:** copies minified JSON
- **Prettify/Minify:** expand or compact the current JSON
- **Escape:** escape JSON by adding `\` to special characters
- **Unescape:** Unescape JSON by removing `\` from special characters
- **Diff Results:** By clicking **'Compare'** (or pressing `Ctrl+Enter`), it will compare the two JSON and highlight lines which are different. The Diff Results will show the changes that will make JSON 1 into JSON 2.
  - **Ignore Array Order toggle** (default = off): having this toggle ON will cause the Diff Results to not flag differences due to array order. The Diff considers objects (not arrays) equivalent independent of order.

    Consider the following example:

    ```json
    obj1 = {"city": "NYC", "name": "Alice", "age": 30}
    obj2 = {"name": "Alice", "age": 30, "city": "NYC"}
    arr1 = [3, 2, 1]
    arr2 = [1, 2, 3]
    ```

    - **ON:** `obj1 == obj2`, `arr1 == arr2`
    - **OFF:** `obj1 == obj2`, `arr1 != arr2`

### Theme toggle

Choose between Dark and Light theme.
