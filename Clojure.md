Clojure Notes
	1 for first one 
	2 for second one fir references

## Variable 
	Immutability

	list:       '(a b :name 12.5)
	vector:     ['a 'b :name 12.5]
	map 		{:name "chas" :age 31}
	set: 		#{1 2 3}

List
	(= '(1 2 3 4 5) (list 1 2 3 4 5))
vec 
	(= [1] (vec '(1)))

set
	(class #{1 2 3}) ; => clojure.lang.PersistentHashSet
	(set [1 2 3 1 2 3 3 2 1 3 2 1]) ; => #{1 2 3}

Maps can be used as functions to do lookups
(= 1 ({:a 1, :b 2} :a))

Add
	(assoc {1 "key"} 2 "key2")

Keys
	(keys/vals {})

## Function 
Function 

	(defn multiply-by-ten [n]  (* 10 n))
	(#(* 15 %) 4))
	(#(* 15 %2) 1 2)

	(((fn [] +)) 4 5))
	((fn [f] (f 4 5)) *)

Taks function as input

	user> ((fn [f] (f "abc")) (fn [s] (str s s s)))
	"abcabcabc"

Conditionals
	(if (false? (= 4 5)) :a :b)

"You may have a multitude of possible paths"

## Let
	(let [x 5]
    (= :your-road (cond (= x 6) :road-not-taken
                        (= x 7) :another-road-not-taken
                        :else :your-road)))


  "In case of emergency, sound the alarms"
  (= :sirens
     (explain-defcon-level :cocked-pistol))

  "But admit it when you don't know what to do"
  (= :say-what?
     (explain-defcon-level :yo-mama)))


http://clojurescriptkoans.com/#runtime-polymorphism/4

"Multimethods allow more complex dispatching"
	(= "Bambi eats veggies."
	 (diet {:species "deer" :name "Bambi" :age 1 :eater :herbivore}))

"Different methods are used depending on the dispatch function result"
	(= "Simba eats animals."
	 (diet {:species "lion" :name "Simba" :age 1 :eater :carnivore}))

"You may use a default method when no others match"
	(= "I don't know what Rich Hickey eats."
	 (diet {:name "Rich Hickey"})))

## Others

### Lazy Seq

	"There is a wide range of ways to generate a sequence"
	(= [1 2 3 4] (range 1 5))

	"The range starts at the beginning by default"
	(= [0 1 2 3 4] (range 5))

	"It's important to only take what you need from a big sequence"
	(= [0 1 2 3 4 5 6 7 8 9]
	 (take 10 (range 100)))

	"You can also limit results by dropping what you don't need"
	(= [95 96 97 98 99]
	 (drop 95 (range 100)))

	"Iteration provides an infinite lazy sequence"
	(= [0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19] (take 20 (iterate inc 0)))

	"Repetition is key"
	(= [:a :a :a :a :a :a :a :a :a :a ]
	 (repeat 10 :a))

	"Iteration can be used for repetition"
	(= (repeat 100 :foo)
	 (take 100 (iterate identity :foo)))
     
### Creating Functions

  "One may know wh
  at they seek by knowing what they do not seek"
  (= [true false true] (let [not-a-symbol? (complement symbol?)]
                  (map not-a-symbol? [:a 'b "c"])))


### Arguments and rest of arguments
    (defn doubler 
	    [f]
	    (fn [& args]
            (* 2 (apply f args))))
            (def double-+ (doubler +))
    (double-+ 1 2 3)

## Notes
REPL
 * Remember switch to the REPL that you are working on.
 * REPL port is storing in dot file.
 * Function only need to load once.
 * in vim lead wiht arrow will move bracket. Lead with w and bracket will add bracket
 * check the source code if you don't understand the function, most of them are macro.
 * Vim: Pradict will auto complete the bracket and keep it balance 
    let paredit_mode = 0    
 * (in-ns 'cenx.eureka.pratice)     

Hard Question
 * P73 Primitive logging system 

TODO
   Configure map multiple select

# Emacs Shortcut    

* M-a	Move back to beginning of sentence
* M-e	Move forward to end of sentence
 
* C-c M-n change current name space in terminal
* C-c C-k Compile current file
* C-c C-k Compile current file
* C-c o Switch to the window
* C-x d Open a Directory


# Database: Postgres
    
 * psql postgres
	    \t
	    \q
 * postgres server: postgres -D /usr/local/var/postgres
 * psql postgre sql default database
 * Under Datomic
     bin/transactor -Xmx6g config/Sprint-config.properties
 * database name on datomic : ripper

 * restore datomic data: bin/datomic -Xmx4g -Xms4g restore-db file:/Users/chuan.du/datomic-dumps/sprint_datomic_20150602  datomic:dev://localhost:4334/ripper


