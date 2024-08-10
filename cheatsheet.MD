Here's a concise Haskell cheat sheet with examples to help you understand key concepts and syntax:

---

### **Basic Types**

```haskell
Int       -- Integer numbers
Float     -- Floating point numbers
Double    -- Double-precision floating point
Bool      -- Boolean values: True or False
Char      -- A single character
String    -- A list of characters (alias for [Char])
```

### **Basic Operations**

```haskell
-- Arithmetic
(+) 1 2           -- 3
(-) 5 2           -- 3
(*) 2 3           -- 6
(/) 7 2           -- 3.5

-- Boolean
(==) 3 3          -- True
(/=) 3 4          -- True
(>)  3 4          -- False
(<)  3 4          -- True

-- Logical
not True          -- False
True && False     -- False
True || False     -- True
```

### **Lists**

```haskell
-- Create a list
[1, 2, 3, 4]               -- List of integers

-- List operations
head [1, 2, 3]             -- 1 (first element)
tail [1, 2, 3]             -- [2, 3] (all but the first)
last [1, 2, 3]             -- 3 (last element)
init [1, 2, 3]             -- [1, 2] (all but the last)
length [1, 2, 3]           -- 3 (length of the list)
reverse [1, 2, 3]          -- [3, 2, 1]

-- List comprehension
[x * 2 | x <- [1, 2, 3]]   -- [2, 4, 6]

-- Concatenation
[1, 2] ++ [3, 4]           -- [1, 2, 3, 4]

-- Cons (prepend)
1 : [2, 3]                 -- [1, 2, 3]
```

### **Tuples**

```haskell
-- Create a tuple
(1, "hello", True)   -- Tuple of an Int, String, and Bool

-- Accessing tuple elements
fst (1, 2)           -- 1 (first element)
snd (1, 2)           -- 2 (second element)
```

### **Functions**

```haskell
-- Function definition
add :: Int -> Int -> Int
add x y = x + y

-- Higher-order function (function taking another function as argument)
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)

-- Example usage
applyTwice (*2) 3     -- 12

-- Anonymous functions (lambda expressions)
(\x -> x + 1) 3       -- 4

-- Partial application
addThree :: Int -> Int -> Int -> Int
addThree x y z = x + y + z
addTwo = addThree 2
addTwo 3 4            -- 9
```

### **Pattern Matching**

```haskell
-- Pattern matching in functions
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- Pattern matching in list processing
sumList :: [Int] -> Int
sumList [] = 0
sumList (x:xs) = x + sumList xs

-- Example usage
sumList [1, 2, 3]     -- 6
```

### **Guards**

```haskell
-- Using guards in function definitions
bmiTell :: Float -> String
bmiTell bmi
  | bmi <= 18.5 = "Underweight"
  | bmi <= 25.0 = "Normal"
  | bmi <= 30.0 = "Overweight"
  | otherwise   = "Obese"

-- Example usage
bmiTell 22.0         -- "Normal"
```

### **Let and Where**

```haskell
-- Using 'let' for local bindings
cylinder :: Float -> Float -> Float
cylinder r h =
  let sideArea = 2 * pi * r * h
      topArea = pi * r^2
  in sideArea + 2 * topArea

-- Using 'where' for local bindings
bmiTell' :: Float -> Float -> String
bmiTell' weight height
  | bmi <= 18.5 = "Underweight"
  | bmi <= 25.0 = "Normal"
  | bmi <= 30.0 = "Overweight"
  | otherwise   = "Obese"
  where bmi = weight / height^2
```

### **Case Expressions**

```haskell
-- Using 'case' for pattern matching
describeList :: [a] -> String
describeList xs = case xs of
  []  -> "Empty list"
  [x] -> "Singleton list"
  _   -> "Longer list"
```

### **Recursion**

```haskell
-- Basic recursive function
factorial' :: Int -> Int
factorial' 0 = 1
factorial' n = n * factorial' (n - 1)

-- Tail recursion
sumList' :: [Int] -> Int
sumList' lst = sumHelper lst 0
  where
    sumHelper [] acc = acc
    sumHelper (x:xs) acc = sumHelper xs (acc + x)
```

### **Map, Filter, and Fold**

```haskell
-- Map: apply a function to all elements in a list
map (+1) [1, 2, 3]        -- [2, 3, 4]

-- Filter: keep elements that satisfy a predicate
filter even [1, 2, 3, 4]  -- [2, 4]

-- Fold: reduce a list to a single value
foldl (+) 0 [1, 2, 3]     -- 6
foldr (+) 0 [1, 2, 3]     -- 6
```

### **Data Types**

```haskell
-- Define a new data type
data Shape = Circle Float | Rectangle Float Float

-- Define a function that works with custom data types
area :: Shape -> Float
area (Circle r) = pi * r^2
area (Rectangle l w) = l * w

-- Example usage
area (Circle 5)            -- 78.54
area (Rectangle 3 4)       -- 12.0
```

### **Type Classes**

```haskell
-- Defining a new type class
class Eq a where
  (==) :: a -> a -> Bool
  (/=) :: a -> a -> Bool
  x /= y = not (x == y)

-- Implementing a type class for a custom data type
data TrafficLight = Red | Yellow | Green

instance Eq TrafficLight where
  Red    == Red    = True
  Yellow == Yellow = True
  Green  == Green  = True
  _      == _      = False

-- Example usage
Red == Red        -- True
Red == Green      -- False
```

### **Monads**

```haskell
-- The Maybe Monad
safeDivide :: Float -> Float -> Maybe Float
safeDivide _ 0 = Nothing
safeDivide x y = Just (x / y)

-- Example usage
result = safeDivide 10 2 >>= \r -> Just (r + 1)
-- Just 6.0

-- The List Monad
pairs = [(x, y) | x <- [1, 2], y <- [3, 4]]
-- [(1, 3), (1, 4), (2, 3), (2, 4)]
```

### **IO Operations**

```haskell
-- Basic IO operation
main :: IO ()
main = do
  putStrLn "What is your name?"
  name <- getLine
  putStrLn ("Hello, " ++ name ++ "!")
```

---

This cheat sheet provides a brief overview of Haskell syntax and concepts, offering a quick reference and examples for common tasks.