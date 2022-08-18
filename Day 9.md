# Exercises of Chapter 4 part 1
## 1. Exercise: repeat
```Ocaml
let rec repeat f n x = if n = 0 then x else repeat f n-1 (f x)
```
## 2. Exercise: product
```Ocaml
let product_left l = List.fold_left ( *. ) 1.0 l
let product_right l = List.fold_right ( *. ) 1.0 l
```
