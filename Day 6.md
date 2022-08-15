# Exercises of Chapter 3 part 3
## 15. Exercise: pokerecord
```Ocaml
type poketype = Normal | Fire | Water ;;

type pokemon = { name : string ; hp : int ; ptype : poketype } ;;

let charizard = { name = "charizard"; hp = 78; ptype = Fire } ;;

let squirtle = { name = "squirtle"; hp = 44; ptype = Water } ;;
```
## 16. Exercise: safe hd and tl
```Ocaml
let safe_hd = function
	| [] -> None
	| x :: _ -> Some x;;
  
let rec safe_tl = function
  | [] ->None
  | x :: [] -> Some x
  | x :: l-> safe_tl l ;;
```
## 17. Exercise: pokefun
```Ocaml
let rec max_hp = function
	| [] ->None
	| x :: l -> match max_hp l with
                | None ->Some x
                | Some y -> Some (if x.hp >= y.hp then x else y) ;;
```
## 18. Exercise: date before
```Ocaml
let is_before date1 date2 =
  let (y1, m1, d1) = date1 in
  let (y2, m2, d2) = date2 in
  y1 < y2 || (y1 = y2 && m1 < m2) || (y1 = y2 && m1 = m2 && d1 < d2)
```
## 19. Exercise: earliest date
```Ocaml
let rec date_before = function
	| [] ->None
	| x :: l -> match date_before l with
                | None ->Some x
                | Some y -> Some (if is_before x y then x else y) ;;
```
## 20. Exercise: assoc list
```Ocaml
let insert k v l = (k, v) :: l ;;

let rec lookup k = function
  | [] -> None
  | (k', v) :: l -> if k = k' then Some v else lookup k l;;

let l = [(1, "one");(2, "two");(3, "three")];;
```
## 21. Exercise: cards
```Ocaml
type suit = Hearts | Spades | Clubs | Diamonds ;;

type rank = Number of int | Ace | Jack | Queen | King ;;

type card = { suit: suit; rank: rank} ;;
```
**Notice:  
Field names must start with uppercase.
**
## 22. Exercise: matching
```Ocaml
let l1 = [None; Some 1; Some 2] ;;
let l2 = [None; Some 1; Some 2] ;;
let l3 = [None; Some 1; Some 2] ;;
let l4 = [Some 1]
(* h :: t1 match any int option list that is not []*)
```
## 23. Exercise: quadrant
```Ocaml
type quad = I | II | III | IV ;;
type sign = Neg | Pos | Zero ;;

let sign x =
  if x > 0 then Pos 
	else if x = 0 then Zero
	else Neg;;

let quadrant : int*int -> quad option = fun (x,y) ->
  match sign x, sign y with
    | (Pos, Pos) -> Some I
    | (Neg, Pos) -> Some II
    | (Neg, Neg) -> Some III
    | (Pos, Neg) -> Some IV
    | _-> None ;;
```
## 24. Exercise: quadrant when
```Ocaml
let quadrant_when : int*int -> quad option = function
  | x, y when x > 0 && y > 0 -> Some I
  | x, y when x < 0 && y > 0 -> Some II
  | x, y when x < 0 && y < 0 -> Some III
  | x, y when x > 0 && y < 0 -> Some IV
  | _ -> None ;;
```
> A guard is the conditional which follows the when, and it means that the pattern match only happens if the pattern matches and the condition in the when-clause is satisfied.  
> match value with  
>| pattern [ when condition ] -> result  
>| pattern [ when condition ] -> result  
> ...  
