- #+BEGIN_PINNED
  Garcia-Molina, H., Ullman, J. D., & Widom, J. (2014). Database systems: the complete book (2nd ed.). Pearson. c2.3
  #+END_PINNED
- Keywords: ==SQL== ==Three kinds of relation== ==Data types== ==Declare table== ==Modify table== ==Keys==
-
- ## Relations in SQL
	- SQL makes a distinction between three kinds of relations:
		- Stored relations, which are called *tables*.
		- *Views*, which are relations defined by computation.
			- These relations are constructed in whole or in part, when needed.
		- Temporary tables, which are constructed by the SQL language processor when it performs its job of executing queries and data modification. These reations are then thrown away.
- ## Data Types
	- Character strings of fixed or varing length.
		- The type `CHAR(n)` and `VARCHAR(n)` both denotes a fixed-length string of up to $n$ characters.
		- `CHAR` implies that short strings are padded to make $n$ characters.
		- `VARCHAR` implies that an endmarker or string-length is used.
	- Bit strings of fixed or varing length.
		- Theses strings are analogous to fixed and varing-length character strings, but their values are strings of bits. `BIT(n)` `BIT VARING(n)`
	- The type `BOOLEAN` denotes an attribute whose value is logical.
		- It has three values: `TRUE` `FALSE` `UNKNOWN`
	- The type `INT` or `INTEGER` denotes typical integer values.
	- Floating-point numbers.
		- `FLOAT` or `REAL` for typical floating-point numbers.
		- `DOUBLE PRECISION` for higher precision.
		- `DECIMAL(n, d)` for real numbers with a fixed decimal point. Values are consist of $n$ decimal digits, with the decimal point assumed to be $d$ positions from the right. E.g. 0123.45 is type `DECIMAL(6, 2)`.
	- `DATE` and `TIME` for datas and times.
- ## Simple Table Declarations
	- The simplest form of declaration of a relation schema consists of the keywords `CREATE TABLE` followed by the name of the relation and a parenthesized, comma-separated list of the attributed names and their types.
	- ```SQL
	  CREATE TABLE Movies(
	  	title		CHAR(100),
	    	year		INT,
	    	length		INT,
	    	genre		CHAR(10),
	    	studioName	CHAR(30),
	    	producerC#	INT
	  );
	  ```
	- ```sql
	  CREATE TABLE MovieStar (
	    	name		CHAR(30),
	    	address		VARCHAR(255),
	    	gender		CHAR(1),
	    	birthdate	DATE
	  );
	  ```
- ## Modifying Relation Schemas
	- `DROP TABLE R;`
		- delete a relation.
	- `ALTER TABLE` has two options:
		- `ADD` followed by an attribute name and its data type.
			- `ALTER TABLE MovieStar ADD phone CHAR(16)`, componet of attribute phone have a default value `NULL`.
		- `DROP` followed by an attribute name.
			- `ALTER TABLE MovieStar DROP birthdate`
- ## Default Values
	- Use keyword `DEFAULT` to set defalt value.
		- `ALTER TABLE MovieStar ADD phone CHAR(16) DEFAULT 'unlisted'`
- ## Declaring Keys
	- There are two declarations that may be used to indicate keyness:
		- a) `PRIMARY KEY`
		- b) `UNIQUE`
	- The effect of declaring a set of attributes $S$ to be a key for relation $R$ either using `PRIMARY KEY` or `UNIQUE` is the following:
		- Two tuples in $R$ cannot agree on all of the attributes in set $S$, unless one of them is `NULL`. Any attempt to insert or update a tuple that violates this rule causes the DBMS to reject the action that caused the violation.
	- If `PRIMARY KEY` is used, then attributes in $S$ are not allowed to have `NULL` as a value for their componets.
	- `NULL` is permitted if the set $S$ is declared `UNIQUE`.
-