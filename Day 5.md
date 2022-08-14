# Exercises of Chapter 3 part 1 
## 8. Exercise: list expressions
```Ocaml
let rec take n l =
  match l with 
  |[] -> []
  |x::l1 -> if n = 0 then [] else x :: take (n - 1) l1;;

let rec drop n l =
  match l with 
  |[] -> []
  |x::l1 -> if n = 0 then l else drop (n - 1) l1;;
```
**Notice:  
The essence of this question is a nested if expression.**

## 9. Exercise: take drop tail
```Ocaml
let rec take_t n l ans =
  match l with 
  |[] -> ans
  |x::l1 -> if n = 0 then ans else take_t (n - 1) l1 (ans @ [x]) ;;

(*fun drop is already tail recursion*)
let drop_t = drop ;; 
```
**Notice:  
Tail recursion refers to calling itself when a function returns. So we need an additional parameter as an accumulator.**

## 11. Exercise: powerset
```Ocaml
let rec powerset s=
  match s with
  | [] -> [ [] ]
  | h :: t -> (List.map (fun x-> h::x) (powerset t)) @ (powerset t)
```
**Notice:  
All subsets of an element result in an empty set and the element itself. On this basis, every time an element is added, all the original subsets face a problem: adding this element and not adding this element. That is to say, after adding an element, all subsets are equal to (all original subsets) + (the result of adding this element to each original subset). 
And about the map function, refer to the [Ocaml manual]( https://v2.ocaml.org/api/List.html)**
> map f [a1; ...; an] applies function f to a1, ..., an, and builds the list [f a1; ...; f an] with the results returned by f.

## 12. Exercise: print int list rec
```Ocaml
let rec print_int_list = function
  | [] -> ()
  | h :: t -> print_endline (string_of_int h); print_int_list t ;;
```
## 13. Exercise: print int list iter
```Ocaml
let print_int_list' lst =
  List.iter (fun x -> print_endline (string_of_int x)) lst ;;
```
## 14. Exercise: student
```Ocaml
let m = {first_name = "yui"; last_name = " kagurazaka"; gpa = 4.0 };;
let name s = s.first_name, s.last_name ;;
let create f l g = {first_name = f; last_name = l; gpa = g };;
```
