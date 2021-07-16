# array.ahk
Conversion of JavaScript's Array methods to AutoHotkey

[![npm](https://img.shields.io/npm/dm/array.ahk?style=for-the-badge&logo=npm)](https://www.npmjs.com/package/array.ahk) [![docs](https://img.shields.io/badge/full-documentation-blue?style=for-the-badge)](https://chunjee.github.io/array.ahk)


AutoHotkey lacks built-in iteration helper methods (as of 1.1.33) to perform many of the common array behaviors found in other languages. This package ports most of JavaScript's Array object methods to AutoHotkey's Array object.

### Ported Methods
* concat
* every
* fill
* filter
* find
* findIndex
* forEach
* includes
* indexOf
* join
* lastIndexOf
* map
* reduce
* reduceRight
* reverse
* shift
* slice
* some
* sort
* splice
* toString
* unshift

### Installation

In a terminal or command line navigated to your project folder:

```bash
npm install array.ahk
```
You may also review or copy the library from [./export.ahk on GitHub](https://raw.githubusercontent.com/chunjee/array.ahk/master/export.ahk)


In your code:

```autohotkey
#Include %A_ScriptDir%\node_modules
#Include array.ahk\export.ahk

msgbox, % [1,2,3].join()
; => "1,2,3"
```

### Usage

`Array.<fn>([params*])`
```autohotkey
; Map to doubled value
arrayInt := [1, 5, 10]
arrayInt.map(func("fn_doubleInt"))
; => [2, 10, 20]

fn_doubleInt(int) {
	return int * 2
}


; Map to object property
arrayObj := [{"name": "bob", "age": 22}, {"name": "tom", "age": 51}]
arrayObj.map(func("fn_returnName"))
; => ["bob", "tom"]

fn_returnName(obj) {
	return obj.name
}


; Method chaining
arrayObj := [{"name": "bob", "age": 22}, {"name": "tom", "age": 51}]
msgbox, % arrayObj.map(func("fn_returnProp").bind("age"))
	.map(func("fn_doubleInt"))
	.join(",")
; => "44,102"

fn_returnProp(prop, obj) {
	return obj[prop]
}
```

### Sorting

JavaScript does not expose start/end or left/right parameters and neither does this sort.

`Array.sort([params*])`
```autohotkey
arrayInt := [11,9,5,10,1,6,3,4,7,8,2]
arrayInt.sort()
; => [1,2,3,4,5,6,7,8,9,10,11]
```
