- #+BEGIN_QUERY
  {:title "Vue"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r4c")]]
  }
  #+END_QUERY