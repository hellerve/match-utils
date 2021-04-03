# match-utils

is a collection of utility macros around `match`.

WIP, let me optimize before using it.

## Usage

```clojure
; let-match lets you do a match bind
(let-match [(Maybe.Just x) (Array.nth &[@"hi"] 0)]
  (println* x)) ; => "hi"

; defn-match allows you to write pattern-matching functions
; here i want to optimize dispatch
(deftype Num
  (I [Int])
  (D [Double]))

(use Num)
(MatchUtils.defn-match add-num
  [(I x) (I y)] (I (+ x y))
  [(D x) (D y)] (D (+ x y))
  [(D x) (I y)] (D (+ x (from-int y)))
  [(I x) (D y)] (D (+ (from-int x) y)))
```

<hr/>

Have fun!
