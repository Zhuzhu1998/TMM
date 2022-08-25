# Exercises of Chapter 4 
## 8. Exercise: more list fun 
```Ocaml
let fun1 l = List.filter (fun s -> String.length s > 3) ll ;;

let fun2 l = List.map (fun x -> x +. 1.0) l ;;

let fun3 s = function
  | [] -> ""
  | x :: xs -> List.fold_left (fun acc e -> acc ^ s ^ e) x xs ;;
```
## 9. Exercise: valid matrix 
```Ocaml
let is_valid_matrix = function
  | [] -> false
  | x :: xs -> let l = List.length x in
               List.for_all (fun e -> l= List.length e) xs ;;
```
## 10. Exercise: row vector add
```Ocaml
let add_row_vectors = List.map2 (+) ;;
```
## 11. Exercise: matrix add
```Ocaml
let add_matrices = List.map2 add_row_vectors
```
