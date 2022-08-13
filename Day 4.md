# Exercises of Chapter 3 part 1 
## 1. Exercise: list expressions
```Ocaml
let _ = [1; 2; 3; 4; 5] ;;

let _ = 1 :: 2 :: 3 :: 4 :: 5 :: [] ;;

let _ = [1] @ [2; 3] @ [4, 5] ;;
```
## 2. Exercise: product
```Ocaml
let rec product l =
    match l with
    | [] -> 1
    | h :: l1 -> h * product l1 ;;
```
## 3. Exercise: concat
```Ocaml
let rec con s =
    match s with
    | [] ->""
    |h :: s1 -> h ^ con s1 ;;
```
## 4. Exercise: product test
```Ocaml
let tests = "test suite for product" >::: [
  "empty" >:: (fun _ -> assert_equal 1 (product []));
  "singleton" >:: (fun _ -> assert_equal 1 (product [1]));
  "two_elements" >:: (fun _ -> assert_equal 6 (sum [2;3]));
] ;;

let _ = run_test_tt_main tests ;;
```
## 5. Exercise: patterns
```Ocaml
let bmatch l =
  match l with
  | [] -> false
  | h :: l1 -> h = "bigred" ;;
    
let nmatch l =
  match l with
  | _ :: _ :: [] -> true
  | _ :: _ :: _ :: _ :: [] -> true
  | _ -> false ;;
  
let ematch l =
  match l with
  | l1 :: l2 :: _ -> l1 = l2
  | _ -> false ;;
```
## 6. Exercise: library
```Ocaml
let fifth l = if (List.length l) >= 5 then List.nth l 4 else 0 ;;

let sort_l l= List.rev (List.sort Stdlib.compare l) ;;
```
## 7. Exercise: library puzzle
```Ocaml
let last_e l = List.nth l (List.length l - 1) ;;

let zeros l = List.exists (fun x -> x = 0) l ;;
```
**Notice:    
Check for [List sacanning]( https://v2.ocaml.org/api/List.html#1_Listscanning).**
>exists f [a1; ...; an] checks if at least one element of the list satisfies the predicate f. That is, it returns (f a1) || (f a2) || ... || (f an) for a non-empty list and false if the list is empty.
