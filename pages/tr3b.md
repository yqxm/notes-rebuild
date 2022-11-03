- #+BEGIN_QUERY
  {:title "算法"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r3b")]]
  }
  #+END_QUERY
-