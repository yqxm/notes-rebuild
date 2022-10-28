query-sort-by:: created-at
query-sort-desc:: false
#+BEGIN_QUERY
{:title "信息的表示和处理"
 :query [:find (pull ?p [*])
         :where 
         [?p :block/name ?name]
         [(clojure.string/starts-with? ?name "r1a1")]]
}
#+END_QUERY

- query-sort-by:: created-at
  query-sort-desc:: false
  #+BEGIN_QUERY
  {:title "练习"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "re1a1")]]
  }
  #+END_QUERY