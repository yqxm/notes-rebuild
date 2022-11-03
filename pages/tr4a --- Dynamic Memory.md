query-sort-by:: created-at
query-sort-desc:: false
#+BEGIN_QUERY
{:title "Classes"
 :query [:find (pull ?p [*])
         :where 
         [?p :block/name ?name]
         [(clojure.string/starts-with? ?name "r4a12")]]
}
#+END_QUERY

-