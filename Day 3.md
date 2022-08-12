# Exercises of Chapter 2 
## 1. Exercise: values
```Ocaml
# 7 * (1 + 2 + 3) ;;
- : int = 42

# "CS " ^ string_of_int 3110 ;;
- : string = "CS3110"
```
## 2. Exercise: operators
```Ocaml
# 42 * 10 ;;

# 3.14 /. 2. ;;

# 4.2 ** 7. ;;
```
**Notice:  
There is no built-in integer exponentiation operator in OCaml.**
## 3. Exercise: equality
```Ocaml
# 42 = 42 ;;
- : bool = true

# "hi" = "hi" ;;
- : bool = true

# "hi" == "hi" ;;
- : bool = false
```
**Notice:  
According to [The OCaml Manual](https://v2.ocaml.org/api/Stdlib.html), "=" is structural equality test and "==" is physical equality test.**
>structural equal  
>e1 = e2 tests for structural equality of e1 and e2. Mutable structures (e.g. references and arrays) are equal if and only if their current contents are structurally equal, even if the two mutable objects are not the same physical object. Equality between functional values raises Invalid_argument. Equality between cyclic data structures may not terminate. Left-associative operator, see Ocaml_operators for more information.  
>physical equal  
>e1 == e2 tests for physical equality of e1 and e2. On mutable types such as references, arrays, byte sequences, records with mutable fields and objects with mutable instance variables, e1 == e2 is true if and only if physical modification of e1 also affects e2. On non-mutable types, the behavior of ( == ) is implementation-dependent; however, it is guaranteed that e1 == e2 implies compare e1 e2 = 0. Left-associative operator, see Ocaml_operators for more information.  

**In OCaml, "x = y" is similar to the "x.equals(y)" in Java.**
## 4. Exercise: 
```Ocaml
# assert true;;
- : unit = ()

# assert false;;
Exception: Assert_failure ("//toplevel//", 1, 0).

# assert (not (2110 = 3110));;
```
**Notice:  
The expression assert e evaluates e. If the result is true, the entire expression evaluates to unit. But if the result is false, an exception is raised.**
## 5. Exercise: if
```Ocaml
# let _ = if 2 > 1 then 42 else 7 ;;
```
## 6. Exercise: double fun
```Ocaml
# let double x = 2 * x ;;
# let _ = assert (double 1 = 2) ;;
```
## 7. Exercise: more fun
```Ocaml
# let cube x = x *. x *. x ;;
# assert (cube 2. = 8.)

# let sign x = if x > 0 then 1
  else if x = 0 then 0
  else -1;;

# let area r = r ** 2 *.3.14 ;;
```
## 8. Exercise: RMS
```Ocaml
# let rms x y = (x *. x +. y *. y) ** 0.5;;
```
## 9. Exercise: date fun
```Ocaml
# let date d m =
  if 1 <= d && d <= 31
  then m = "Jan" || m = "Mar" || m = "May" || m = "Jul"
     || m = "Aug" || m = "Oct" || m = "Dec"
  else if 1 <= d && d <= 30
  then m = "Apr" || m = "Jun" || m = "Sept" || m = "Nov"
  else if 1 <= d && d <= 28
  then m = "Feb"
  else false
```
## 10. Exercise: fib
```Ocaml
# let rec fib n =
  if n = 0 then 0
  else if n = 1 then 1
  else fib (n-1) + fib (n-2);
```
## 11. Exercise: fib fast
```Ocaml
# let rec h n pp p =
  if n = 1 then p
  else h (n-1) p (pp+p)
# let fib_fast n =
  if n=0 then 0
  else h n 0 1
```
## 12. Exercise: poly types
```Ocaml
# let f x = if x then x else x;;
val f : bool -> bool = <fun>
# let g x y = if y then x else x;;
val g : 'a -> bool -> 'a = <fun>
# let h x y z = if x then y else z ;;
val h : bool -> 'a -> 'a -> 'a = <fun>
# let i x y z = if x then y else y ;;
val i : bool -> 'a -> 'b -> 'a = <fun>
```
**Notice:**  
**“If x/if y” indicates that x/y must be a bool;‘a means any type, so does ‘b.  
As for the third expression, y and z must be the same type. Because “then” and “else” must have same return type.  
As for the forth expression, b and z can be any type, and they can be different.**
## 13. Exercise: divide
```Ocaml
# let divide numerator denominator = numerator /. denominator ;;
```
## 14. Exercise: associativity
```Ocaml
# add 5 1;;
- : int = 6
# add 5;;
- : int -> int = <fun>
# (add 5) 1;;
- : int = 6
# add (5 1);;
Error: This expression has type int
       This is not a function; it cannot be applied.
```
**Notice:  
add 5 is a anonymous function.  
add 5 <=> let _ y = 5 + y  
add (5 1) 5 is viewed as a function.**
## 15. Exercise: average 
```Ocaml
# let (+/.) a b = (a +. b) /. 2.
```
## 16. Exercise: hello world
```Ocaml
# print_endline "Hello world!";;
hello world!
- : unit = ()
# print_string "Hello world!";;
hello world!- : unit = ()

```
