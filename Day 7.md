# Exercises of Chapter 3 part 4 
## 25. Exercise: depth 
```Ocaml
type 'a tree =
  | Leaf
  | Node of 'a * 'a tree * 'a tree;;
let rec depth = function
  | Leaf -> 0
  | Node (_, left, right) -> if depth left > depth right 
then depth left + 1 
else depth right + 1;;
```
## 26. Exercise: shape
```Ocaml
let rec same_shape t1 t2 =
  match t1, t2 with
  | Leaf, Leaf -> true
  | Leaf, _ -> false
  | _, Leaf -> false
  | Node (_,l1,r1), Node (_,l2,r2) -> (same_shape l1 l2) && (same_shape r1 r2)
```
## 27. Exercise: list max exn
```Ocaml
let list_max = function
   |[]->raise(Failure "list_max")
   |h::t->let rec not_empty_list x = function
        |[]->x
        |h1::t1 ->not_empty_list(Stdlib.max x h1) t1
                  in not_empty_list h t;;
```
**Notice:  
Refer more about “Exceptions” in [3.10](https://cs3110.github.io/textbook/chapters/data/exceptions.html).**
## 28. Exercise: list max exn string 
```Ocaml
let list_max_string l =
  try string_of_int ( list_max l ) with
  | Failure _ -> "empty"
```
**Notice:**
> To catch an exception, use this syntax:  
>try e with  
>| p1 -> e1  
>| ...  
>| pn -> en  
> The expression e is what might raise an exception. If it does not, the entire try expression evaluates to whatever e does. If e does raise an exception value v, that value v is that matched against the provide patterns, exactly like match expression.  

**The type of p1…pn is exn (Failure).**
## 29. Exercise: list max exn ounit 
```Ocaml
let tests = "test suite for list_max" >::: [
  "empty" >:: (fun _ -> assert_raises (Failure "list_max") (list_max []);
  "not_empty" >:: (fun _ -> assert_equal 1 (list_max [-1;0;1]));
] ;;

let _ = run_test_tt_main tests ;;
```
## 30. Exercise: is_bst
```Ocaml
type 'a tree =
    | Leaf
    | Node of 'a * 'a tree * 'a tree;;

let is_bst_helper = function
  | Leaf->true
  | Node (x, l , r)-> match l , r with
                    | Leaf,Leaf -> true
                    | Node(lvalue,_,_),Leaf -> lvalue < x && is_bst_helper l 
                    | Leaf,Node(rvalue,_,_) -> rvalue > x && is_bst_helper r 
                    | Node(lvalue,_,_), Node(rvalue,_,_) -> rvalue > x && lvalue < x && is_bst_helper l && is_bst_helper r;;


let is_bst t= 
  match is_bst_helper t with
    | true -> "The given tree satisfies the binary search tree invariant"
    |false -> "The given tree does not satisfie the binary search tree invariant"
```
**Notice:  
The binary search tree invariant means that value of left child node must be less than the value of father node and value of right child node must be greater than the value of father node.**
## 31. Exercise: quadrant poly
```Ocaml
let sign_poly x =
  if x < 0 then `Neg
  else if x = 0 then `Zero
  else `Pos
let quadrant x y=
  match sign_poly x, sign_poly y with
  | `Pos, `Pos -> Some `I
  | `Neg, `Pos -> Some `II
  | `Neg, `Neg -> Some `III
  | `Pos, `Neg -> Some `IV
  | _ -> None
```
