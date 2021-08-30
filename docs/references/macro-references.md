---
id: macro-references
title: Macro References
---

Here, you'll find information about macros, what they do, their properties and examples. 

You can jump to any macro through the sidebar.

---

## Input Macros

### `abs`

Returns the absolute value of a specified number.

#### Arguments

| Argument      | Description                                                                             |
|---------------|-----------------------------------------------------------------------------------------|
| `float`       | A number that is greater than or equal to MinValue, but less than or equal to MaxValue. |

#### Returns

`float` - an absolute number.

#### Example
```
abs('-50')
```

##### Output
```
50
```

---

### `contains`

Determines whether a given collection contains a value

#### Arguments

| Argument      | Description          |
|---------------|----------------------|
| `IEnumerable` | Collection to check. |
| `object`      | Item to look for.    |

#### Returns

`bool` - True if collection does contain an item.

#### Example

Given a variable: `fruits` = ['apple', 'banana', 'orange']

```
contains(%fruits%, 'apple')
```

##### Output
```
True
```

---

### `count`

Counts number of items in a collection (array, list etc.).

#### Arguments

| Argument      | Description           |
|---------------|-----------------------|
| `IEnumerable` | Collection to measure |

#### Returns

`int` - number of items in a collection

#### Example

Given a variable: `fruits` = ['apple', 'banana', 'orange']

```
count(%fruits%)
```

##### Output
```
3
```

---

### `decr`

Returns a value decremented by 1.

#### Arguments

| Argument     | Description                              |
|--------------|------------------------------------------|
| `long`     | Value that will be decremented. |

#### Returns

`decimal` - Decremented value.

#### Example

```
decr(10)
```

##### Output
```
9
```

---

### `envar`

Retrieves a value of an environment variable.

#### Arguments

| Argument     | Description                              |
|--------------|------------------------------------------|
| `string`     | Name of the environment variable. |

#### Returns

`string` - Value of an environment variable.

#### Example

Given that a machine has an environment variable `ACCOUNT_USERNAME` with a value of `Heavy_Weapons_Guy`.

```
envar("ACCOUNT_USERNAME")
```

##### Output
```
"Heavy_Weapons_Guy"
```

---

### `equal`

Determines whether a both objects are equal to one another.

#### Arguments

| Argument   | Description                |
|------------|----------------------------|
| `object`   | First object to compare.   |
| `object`   | Second object to compare.  |

#### Returns

`bool` - True if objects are equal to one another.

#### Example

```
count('fruits', 'vegetables')
```

##### Output
```
False
```

---

### `get`

Gets a specific item from an array from a given index.

#### Arguments

| Argument      | Description        |
|---------------|--------------------|
| `IEnumerable` | Target collection  |
| `int`         | Index of an item   |

#### Returns

`object` - an item at a specified index of a collection.

#### Example

Given a variable: `fruits` = ['apple', 'banana', 'orange']

```
get(%fruits%, 2)
```

##### Output
```
orange
```

---

### `get_git_current_branch`

Returns name of a currently check out branch in a given Git repository.

#### Arguments

| Argument      | Description                                                                             |
|---------------|-----------------------------------------------------------------------------------------|
| `string`      | Path to the Git repository.. |

#### Returns

`string` - commit hash.

#### Example
```
get_git_current_branch("C:/Path/To/Correct/Git/Repository/Directory")
```

##### Output
```
stable
```

---

### `get_git_last_commit_hash`

Returns hash of the latest commit of a given Git repository.

#### Arguments

| Argument      | Description                                                                             |
|---------------|-----------------------------------------------------------------------------------------|
| `string`      | Path to the Git repository. |

#### Returns

`string` - commit hash.

#### Example
```
get_git_last_commit_hash("C:/Path/To/Correct/Git/Repository/Directory")
```

##### Output
```
fbbf816046bd1dd6f076d35e051fed07964d5add
```

---

### `has_key`

Determines whether a given EditorPrefs key exists.

#### Arguments

| Argument      | Description                  |
|---------------|------------------------------|
| `string`      | Name of the key to look for. |

#### Returns

`bool` - True if EditorPrefs of given key exists.

#### Example
```
has_key('key_that_does_not_exist')
```

##### Output
```
False
```

---

### `if`

Returns the choice between 2 objects depending on a boolean value.

#### Arguments

| Argument     | Description                              |
|--------------|------------------------------------------|
| `bool`       | Boolean that determines which of the other parameters to return. |
| `object`     | Parameter that will be returned if boolean is `true`. |
| `object`     | Parameter that will be returned if boolean is `false`. |

#### Returns

`object` - Returned object depending on the boolean value.

#### Example
```
if(true, "Foo", "Bar")
```

##### Output
```
"Foo"
```

---

### `incr`

Returns a value incremented by 1.

#### Arguments

| Argument     | Description                              |
|--------------|------------------------------------------|
| `long`     | Value that will be incremented. |

#### Returns

`decimal` - Incremented value.

#### Example

```
incr(10)
```

##### Output
```
11
```

---

### `invert`

Returns an inverted boolean.

#### Arguments

| Argument      | Description                      |
|---------------|----------------------------------|
| `bool`        | Boolean which will be inverted.  |

#### Returns

`bool` - An inverted boolean.

#### Example
```
invert('true')
```

##### Output
```
False
```

---

### `is_git_repo`

Checks whether given path contains a valid Git repository.

#### Arguments

| Argument      | Description                                                                             |
|---------------|-----------------------------------------------------------------------------------------|
| `string`      | Path to the Git repository.. |

#### Returns

`bool` - `true` if given path does contain a repository.

#### Example
```
is_git_repo("C:/Path/To/Correct/Git/Repository/Directory")
```

##### Output
```
true
```

---

### `length`

Counts the number of characters in a string.

#### Arguments

| Argument      | Description                              |
|---------------|------------------------------------------|
| `string`      | String which characters will be counted. |

#### Returns

`int` - Number of characters a given string has.

#### Example
```
length('four')
```

##### Output
```
4
```

---

### `load`

Loads an asset file from a given path

#### Arguments

| Argument      | Description                           |
|---------------|---------------------------------------|
| `string`      | Path to the asset that will be loaded |

#### Returns

`UnityEngine.Object[]` - an array of loaded Unity objects.

#### Example
```
load('Assets/ExampleFolder/)
```

##### Output
```
UnityEngine.Object[]
```

---

### `path`

Resolves path with a wildcard in it.

#### Arguments

| Argument      | Description         |
|---------------|---------------------|
| `string`      | Path to to resolve. |

#### Returns

`string[]` - Array of resolved paths

#### Example

Given the following project structure:

```
Assets/
├── Scenes/
│   ├── scene1.unity
│   ├── scene2.unity
│   ├── scene3.unity
│   └── scene4.unity
└── Scripts/
    ├── PlayerController.cs
    ├── EnemyController.css
    └── InventoryManager.cs
```
Formula
```
path('%AssetsDir%/*.cs', true)
```

##### Output (if contents printed out)
```
Assets/PlayerController.cs
Assets/EnemyController.cs
Assets/InventoryManager.cs
```

---

### `peel`

Returns a value of a field/property associated with an object by name. This method uses reflection, and, therefore, can be performance intensive if used a lot.

#### Arguments

| Argument      | Description                                                                             |
|---------------|-----------------------------------------------------------------------------------------|
| `object`       | Object from which data will be extracted. |
| `string`       | Name of the field/property that's associated with the object. |

#### Returns

`object` - value of extracted field/property.

#### Example
```
peel("Hello World", Length)
```

##### Output
```
11
```

##### Explanation

The first argument "Hello World" is of `System.String` type, which has a property named `Length`, which returns an exact length of the "Hello World" string, which is 11 (including whitespace).

---

### `percentage`

Gets the value between 0 and 100 to specify percentage progress between 2 values.

#### Arguments

| Argument     | Description    |
|--------------|----------------|
| `float`      | First value    |
| `float`      | Second value   |

#### Returns

`int` - a value between 0 and 100.

#### Example
```
percentage(50, 1000)
```

##### Output
```
5
```

---

### `pretty`

Prettifies a string.

#### Arguments

| Argument     | Description                    |
|--------------|--------------------------------|
| `string`     | String that will be prettified |

#### Returns

`string` - Prettified string

#### Example
```
pretty('helloThere')
```

##### Output
```
Hello There
```

---

### `read`

Returns contents of a text file.

#### Arguments

| Argument      | Description            |
|---------------|------------------------|
| `string`      | Path of a file to read |

#### Returns

`string` - contents of a text file.

#### Example

Given the following text file located at `C:/Path/To/shopping_list.txt`:

```
Shopping List:
- apples
- bananas
- oranges
```

Formula
```
read('C:/Path/To/shopping_list.txt')
```

##### Output

```
Shopping List:
- apples
- bananas
- oranges
```

---

### `split`

Splits a string and puts contents into a collection.

#### Arguments

| Argument      | Description                                 |
|---------------|---------------------------------------------|
| `string`      | String that will be split                   |
| `string`      | Character(s) a string will be separated by  |

#### Returns

`IEnumerable<string>` - collection of split strings.

#### Example
```
split('this;is;pretty;neat', ';')
```

##### Output (if contents printed out)
```
this
is
pretty
neat
```

---

### `sum`

Sums 2 values together.

#### Arguments

| Argument      | Description   |
|---------------|---------------|
| `float`       | First value   |
| `float`       | Second value  |

#### Returns

`float` - a sum of 2 values

#### Example

```
sum('3', '2')
```

##### Output
```
5
```

---

## Output Macros

### `addto`

Add a resultant item to a target collection.

#### Arguments

| Argument      | Description           |
|---------------|-----------------------|
| `IEnumerable` | Collection to add to  |

#### Example

Given a variable: `fruits` = ['apple', 'banana', 'orange']

Given the output value: "tomato"

```
addto(%fruits%)
```

##### Result

`fruits` = ['apple', 'banana', 'orange', 'tomato']

---

### `invert`

Inverts a boolean before assigning it to a target variable.

#### Arguments

| Argument      | Description                    |
|---------------|--------------------------------|
| `bool`        | Boolean that will be inverted. |

#### Example

Given the output value = "True"

```
invert(%new_variable%)
```

##### Result

`new_variable` = "False"