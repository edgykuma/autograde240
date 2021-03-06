# autograde240
*A tool for autograding 18240 assignments*

Written in Python, ported to Python3.

## Requirements
- Python 3.X
- Synopsys VCS

## Usage
Check usage by running
```bash
autograde240 -h
```

Ensure your file hierarchy looks like the following:
```
.
+-- STAFF
|   +-- config.json
|   +-- *.sv
+-- studentID1
|   +-- *.sv
+-- studentID2
|   +-- *.sv
...
```
Where the `STAFF` and `studentID#` folders are in the same level. **This must be
satisfied for the tool to work properly**.

Run the `autograde240` executable inside of the `STAFF` folder.

## Config files
All config files must be of the `.json` format, and structured like so:
```json
{
    "assignment": "hwX",
    "rubric": [
        {
            "problem": 1,
            "files": null,
            "modules": null,
            "tb_files": null,
            "testbenches": null
        }
    ]
}
```
### `assignment`
Type: `string`

The name of the assignment being graded.

### `rubric`
Type: `[object]`

An array of rubric elements, each element describing some part of the problem.

#### `problem`
Type: `int`

Number of problem being graded

#### `files`
Type: `[str]`

Array of files that each student should have submitted.

#### `modules`
Type: `[str]`

Array of module names that students should have written.

#### `tb_files`
Type: `[str]`

Array of files the autograder testbenches are described in. *These files should
be located inside of the `STAFF` folder*.

#### `testbenches`
Type: `[str]`

Array of testbench module names.

## Testbench requirements
The requirements for the autograder testbenches are quite lax. You can do
whatever you wish, so long as you output the string `error` (case-insensitive)
whenever the solution is wrong.
