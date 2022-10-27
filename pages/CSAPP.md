query-sort-by:: created-at
query-sort-desc:: false
#+BEGIN_QUERY
{:title "Computer Systems: A Programmer's Perspective"
 :query [:find (pull ?p [*])
         :where 
         [?p :block/name ?name]
         [(clojure.string/starts-with? ?name "r1a1")]]
}
#+END_QUERY

-