# Exercises of Chapter 7 
## 1. Exercise: spec game 
```Ocaml
type stu = {
	name : string ;
	mutable gpa : float
}
let alice = {name = "Alice"; gpa = 3.7};;
alice.gpa <- 4.0;;
```
**Notice:**  
**! is the dereference operator in OCaml and is kind of like * in C.  
The first letter of the variable name cannot be capitalized. If it is capitalized, it will be treated as a constructor in the union type.**  
>let Alice = …  
>Error: Unbound constructor Alice

## 2. Exercise: inc fun
```Ocaml
let ans = 
  let inc = ref (fun x -> x + 1) in !inc 3109 ;;
```
## 3. Exercise: inc fun
```Ocaml
let ( +:= ) x y = x := !x + y;;
```
**Notice:**  
**Its type should be int ref -> int -> unit.  
The type of  “:= “ is “- : unit = ()”**  
## 4. Exercise: physical equality
```Ocaml
let x = ref 0;;
let y = x;;
let z = ref 0;;
# x == y;;
- : bool = true
# x == z;;
- : bool = false
# x = y;;
- : bool = true
# x = z;;
- : bool = true
# x:= 1;;
- : unit = ()
# x = y;;
- : bool = true
# x = z;;
- : bool = false
```
## 5. Exercise: norm
```Ocaml
type vector = float array;;
let norm x =
  x
  |> Array.map(fun y -> y**2.)
  |> Array.fold_left (+.) 0.
  |> sqrt;;
```
## 6. Exercise: normalize
```Ocaml
let normalize x =
   let nx = norm x in 
   Array.iteri (fun i e -> x.(i) <- e /. nx) x
```
**Notice:**  
**The deference between iteri and iter is that iteri is applied to the index of the element as first argument. Iter only takes the elements as argument. Here, we need to change the value of element, so we need index to change x.(i).**
