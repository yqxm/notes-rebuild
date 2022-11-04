- #+BEGIN_QUERY
  {:title "CNASA"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r10a")]]
  }
  #+END_QUERY
-