# Closures Lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

Write a function named `applyKTimes` that takes an integer `K` and a closure and calls the closure K times. The closure will not take any parameters and will not have a return value.

Function Definition:
func applyKTimes(_ K: Int, _ closure: () -> ())

Example:
Input:

```swift
applyKTimes(3) {
    print("Hello Closures!")
}
```
Output:

```swift
Hello Closures!
Hello Closures!
Hello Closures!
```
```swift
func applyKTimes(_ K: Int, _ closure: () -> ()) {
for _ in 1...K {
closure()
}
}

applyKTimes(3) {
print("Hello Closures!")
}
```

## Question 2

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

`let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`

```swift
let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]

let multiples = numbers.filter() { $0 % 3 == 0 }
print(multiples)
```

## Question 3

Find the largest number from `numbers` and then print it. Use `reduce` to solve this exercise.

Example:
Input: `let numbers = [4, 7, 1, 9, 6, 5, 6, 9]`

Output: `9`

```swift
let compareForMax = { (x: Int,y: Int) -> Int in
if x > y {
return x
}
return y
}

let largesNum = numbers.reduce(Int.min, {compareForMax($0, $1)})
print(largesNum)
```

## Question 4

Join all the strings from `strings` into one using `reduce`. Add spaces in between strings. Print your result.

Example:
Input: `let strings = ["We", "Heart", "Swift"]`

Output: `"We Heart Swift"`

```swift
let altogetherNow = strings.reduce("", {if $0 == "" {return $1} else {return $0 + " " + $1}})
print(altogetherNow)
```

## Question 5

`let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]`

a. Use `sortedBy` to sort `cities` in alphabetical order.

```swift
let alphabetized = cities.sorted(by: {$0 < $1})
print(alphabetized)
```

b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.

```swift
let secondLetter = cities.sorted(by: {(a: String, b: String) -> Bool in
return a.dropFirst() < b.dropFirst()
})
print(secondLetter)
```

c. Use `sortedBy` to sort `cities` in order of the length of the city name.

```swift
let sortByLength = cities.sorted(by: {(a,b) -> Bool in
return a.count < b.count
})
print(sortByLength)

```

## Question 6

`let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]`

a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.

```Swift
let sortByPopulation = citiesWithPopulation.sorted(by: {(a: (String,Int), b: (String,Int)) -> Bool in
return a.1 < b.1
})
print(sortByPopulation)
```

b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.

```swift
let sortByLastCharacter = citiesWithPopulation.sorted(by: {(a: (String,Int), b: (String,Int)) -> Bool in
var value = Bool()
if let realA = a.0.last {
if let realB = b.0.last {
value = realA > realB
}
}
return value
})
print(sortByLastCharacter)
```

## Question 7

Sort `numbers` in ascending order by the number of divisors. If two numbers have the same number of divisors the order in which they appear in the sorted array does not matter.

`var numbers = [1, 2, 3, 4, 5, 6]`

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output:

```swift
numbers = [1, 2, 3, 5, 4, 6]
// 1 has one divisor
// 2, 3 and 5 have 2
// 4 has 3 divisors
// 6 has 4 divisors

// [1, 5, 2, 3, 4, 6] would also have been a valid solution
```

```swift
func numberOfDivisors (x: Int) -> Int {
var count = 0
for i in 1...x {
if x % i == 0 {
count += 1
}
}
return count
}
let divisors = {(a: Int, b: Int) -> Bool in
return numberOfDivisors(x: a) < numberOfDivisors(x: b)
}
let sortByDivisors = numbers.sorted() {divisors($0, $1)}
print(sortByDivisors)
```

## Question 8

Find the sum of the squares of all the odd numbers from `numbers` and then print it.

`var numbers = [1, 2, 3, 4, 5, 6]`

a. Write code that removes all the odd numbers from the array.

```swift
let oddNumOut = numbers.filter({$0 % 2 != 0 })
print(oddNumOut)

//or
func oddNumOutFunc(arr:[Int]) -> [Int] {
var newArr: [Int] = []
for a in arr {
if a % 2 != 0 {
newArr.append(a)
}
}
return newArr
}
print(oddNumOutFunc(arr: numbers))
```

b. Write code that squares all the numbers in the array.

```swift
let squareAll = numbers.map({(a) -> Int in a * a })
print(squareAll)

//or
func squareAllFunc(arr:[Int]) -> [Int] {
var newArr: [Int] = []
for a in arr {
newArr.append(a * a)
}
return newArr
}
print(squareAllFunc(arr: numbers))
```
c. Write code that finds the sum of the array.

```swift
let sum = numbers.reduce(0, +)
print(sum)

//or
func sumFunc(arr:[Int]) -> Int {
var newAns = 0
for a in arr {
newAns += a
}
return newAns
}
print(sumFunc(arr: numbers))
```

d. Now use `map`, `filter` and `reduce` to solve this problem.

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output: `35 // 1 + 9 + 25 -> 35`

```swift
let oddSquareSum = numbers.filter({$0 % 2 != 0 }).map({(a) -> Int in a * a }).reduce(0, +)
print(oddSquareSum)
```

## Question 9

Implement a function `forEach(array: [Int], _ closure: Int -> ())` that takes an array of integers and a closure and runs the closure for each element of the array.

Example:
Function with Input:

```swift
forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

Output:

```swift
1
4
9
16
```

```swift
func forEach(array: [Int], _ closure: (Int) -> ()) {
for a in array{
closure(a)
}
}

forEach(array: [1, 2, 3, 4]) {
print($0 * $0)
}
```

## Question 10

Implement a function `combineArrays` that takes 2 arrays and a closure that combines 2 Ints into a single Int. The function combines the two arrays into a single array using the provided closure. Assume that the 2 arrays have equal length.

Example:
Input:

```swift
var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
combineArrays(array1,array2) {
    $0 * $1
}
```

Output: `[5,10,15,12]`

```swift
func combineArrays(array1: [Int], array2: [Int], _ closure: (Int,Int) -> (Int)) -> [Int] {
var newArray: [Int] = []
let lastIndex = array1.count - 1
for a in 0...lastIndex {
let new = closure(array1[a],array2[a])
newArray.append(new)
}
return newArray
}

var answer = combineArrays(array1: array1,array2: array2) {
$0 * $1
}
print(answer)
```

## Question 11

a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

`let theInts = [1, 2, 3, 44, 555, 6600, 10763]`

```swift
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
func intsToStrings(arrayOfInts: [Int]) -> [String] {
let stringArray = arrayOfInts.map({(a) -> String in
return String(a)
})
return stringArray
}
intsToStrings(arrayOfInts: theInts)
```

b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

```swift
let asString = {(a: Int) -> String in
return String(a)
}

func intsToStrings(arrayOfInts: [Int]) -> [String] {
var stringArray:[String] = []
for a in arrayOfInts {
let new = asString(a)
stringArray.append(new)
}
return stringArray
}
```

c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

```swift
let evenOdd = {(a: Int) -> String in
return a % 2 == 0 ? "even" : "odd"
}

func intsToStrings(arrayOfInts: [Int]) -> [String] {
var stringArray:[String] = []
for a in arrayOfInts {
let new = evenOdd(a)
stringArray.append(new)
}
return stringArray
}

```

d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

```swift
let englishWords = {(a:Int) -> String in
var value = String()
let stringDigit = String(a)
let english = ["0":"zero","1":"one","2":"two","3":"three","4":"four","5":"five","6":"six","7":"seven","8":"eight","9":"nine"]
for i in stringDigit {
if let unwrap = english["\(i)"] {
value = value + " " + unwrap
}
}
return value
}

func intsToStrings(arrayOfInts: [Int]) -> [String] {
var stringArray:[String] = []
for a in arrayOfInts {
let new = englishWords(a)
stringArray.append(new)
}
return stringArray
}

intsToStrings(arrayOfInts: theInts)
```

e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.

Example:
Input:

```swift
let a = intsToStrings(arr: theInts, toString: asString)
let b = intsToStrings(arr: theInts, toString: evenOdd)
let c = intsToStrings(arr: theInts, toString: englishWords)
```

Output:

```swift
a) ["1", "2", "3", "44", "555", "6600", "10763"]
b) ["odd", "even", "odd", "even", "odd", "even", "odd"]
c) ["one ", "two ", "three ", "four four ", "five five five ", "six six zero zero ", "one zero seven six three "]
```
```swift
let a = theInts.map({(a:Int) -> String in
String(a)})
let b =  theInts.map({(a:Int) -> String in
return a % 2 == 0 ? "even" : "odd"
})
let c = theInts.map({(a:Int) -> String in
let stringIt = String(a)
var answer = ""
let english = ["0":"zero","1":"one","2":"two","3":"three","4":"four","5":"five","6":"six","7":"seven","8":"eight","9":"nine"]
for i in stringIt {
if let unwrap = english["\(i)"] {
answer = answer + "\(unwrap) "
}
}
return answer
})
print(a)
print(b)
print(c)
```


## Question 12

`let myArray = [34,42,42,1,3,4,3,2,49]`

a) Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.

```swift
let mySortedArray = myArray.sort(ascendingOrder)
let ascendingOrder =

let ascendingOrder = {(x:Int,y:Int) -> Bool in x < y}
let mySortedArray = myArray.sorted(by: ascendingOrder)
```

b) Sort `myArray` in descending order by defining the constant `descendingOrder` below.

```swift
let mySecondSortedArray = myArray.sort(descendingOrder)
let descendingOrder =

let descendingOrder = {(x:Int,y:Int) -> Bool in x > y}
let mySecondSortedArray = myArray.sorted(by: descendingOrder)
```


## Question 13

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

```swift
let compareThirdElement = {(x:[Int],y:[Int]) -> Bool in
return x[2] < y[2]
}
let sortedArrayOfArrays = arrayOfArrays.sorted(by: compareThirdElement)
```

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.


## Question 14

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a) Sort the string below in descending order according the dictionary `letterValues`:

`var codeString = "aldfjaekwjnfaekjnf"`

```swift
let descending = {(x:Character, y:Character) -> Bool in
var ans = true
if let unwrapX = letterValues["\(x)"],let unwrapY = letterValues["\(y)"] {
ans = unwrapX > unwrapY
}
return ans
}
var sortingWithDict = String(codeString.sorted(by: descending))
print(sortingWithDict)
```
b) Sort the string below in ascending order according the dictionary `letterValues`

`var codeStringTwo = "znwemnrfewpiqn"`

```swift
let ascending = {(x:Character, y:Character) -> Bool in
var ans = true
if let unwrapX = letterValues["\(x)"],let unwrapY = letterValues["\(y)"] {
ans = unwrapX < unwrapY
}
return ans
}

var sortingAgain = String(codeStringTwo.sorted(by: ascending))
```

## Question 15

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
("Claudio", "Monteverdi"),
("Duke", "Ellington"),
("W. A.", "Mozart"),
("Nicolai","Rimsky-Korsakov"),
("Scott","Joplin"),
("Josquin","Des Prez")]
```

Sort the array of tuples by last name. Print the sorted array using string interpolation so that the output looks like:

```swift
Bach, Johann S.
Des Prez, Josquin
...etc

let sortingTuple = {(x:(String,String),y:(String,String)) -> Bool in
return x.1 < y.1
}

var tupleByLastName = firstAndLastTuples.sorted(by: sortingTuple)
for i in tupleByLastName {
print("\(i.1), \(i.0)")
}
```

## Question 16

a) Write a function called `myFilter` that takes an array of Doubles and a closure as parameters and returns an array of Doubles. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

`let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]`

```swift
func myFilter(arr: [Double], _ closure: (Double) -> Bool) -> [Double] {
var newArr: [Double] = []
for a in arr {
if closure(a) {
newArr.append(a)
}
}
return newArr
}
```

b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.

```swift
let biggerThanTen = {(x: Double) -> Bool in
return x >= 10.0
}

print(myFilter(arr: theDoubles) {biggerThanTen($0)})
```

c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.

```swift
let wholeNumber = {(x:Double) -> Bool in
return x.truncatingRemainder(dividingBy: 1.0) == 0
}

print(myFilter(arr: theDoubles) {wholeNumber($0)})
```
d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.

```swift
let justEven = {(x:Double) -> Bool in
return Int(x) % 2 == 0
}

print(myFilter(arr: theDoubles) {justEven($0)})
```
e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.

Example
Input:

```swift
let a = myFilter(arr: theDoubles, filter: biggerThanTen)
let b = myFilter(arr: theDoubles, filter: wholeNumber)
let c = myFilter(arr: theDoubles, filter: justEven)
```

output:

```swift
a. [11.45, 58.65, 66]
b. [4, 66, 5]
c. [4, 58.65, 66]
```
```swift
print(theDoubles.filter(biggerThanTen))
print(theDoubles.filter(wholeNumber))
print(theDoubles.filter(justEven))
```
