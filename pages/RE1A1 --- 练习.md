- #+BEGIN_QUERY
  {:title "练习"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "re1a1")]]
  }
  #+END_QUERY
-