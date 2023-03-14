create a object from a class

```
# Learn Pharo while implementing a LinkedList

Pharo is a developing programming language. It is developed, highly following OOP principles.

LinkedList is a type of list. More information about LinkedList can be found here.

|c|
c := Counter new.
c count: 7.
c count
```

call a method in a obj

```
c count: 7.
```

add an initializing method to a class

```
initialize

	super initialize.
	count := 0
```
