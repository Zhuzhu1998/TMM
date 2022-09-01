# Exercises of Chapter 7 
## 9. Exercise: init matrix
```Ocaml
let init_matrix n o f =
   Array.init n (fun i -> Array.init o (fun j -> f i j))
```
**Notice:**  
**Refer to [Array.init](https://v2.ocaml.org/api/Array.html#VALinit)**  
>init n f returns a fresh array of length n, with element number i initialized to the result of f i. In other terms, init n f tabulates the results of f applied to the integers 0 to n-1.


## 10. Exercise: doubly linked list 
```Ocaml
(** An ['a node] is a node of a mutable doubly-linked list.
    It contains a value of type ['a] and optionally has
    pointers to previous and/or next nodes. *)
type 'a node = {
  mutable prev : 'a node option;
  mutable next : 'a node option;
  value : 'a
}

(** An ['a dlist] is a mutable doubly-linked list with elements
    of type ['a].  It is possible to access the first and
    last elements in constant time.
    RI: The list does not contain any cycles. *)
type 'a dlist = {
  mutable first : 'a node option;
  mutable last : 'a node option;
}

let empty_list () = {first=None; last=None}

let insert_first l n =
   n.next <- l.first;
   l.first <- Some n

let insert_last l n =
   n.prev <- l.last;
   l.last <- Some n
```
