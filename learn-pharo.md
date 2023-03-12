create a object from a class

```
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
