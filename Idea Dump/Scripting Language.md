
Will have C like syntax


# Properties
```csharp
// auto property
public get set float MyProperty;
public get private set float MyProperty;

// getter and setter
public get float MyProperty {
	return _internalField;
}

public set float MyProperty {
	_internalField = value;
}
```

# Null Checking
```csharp
if (MyObject) DoSomething();
```

# Collection Initializer
```csharp
float[] myArray = [0, 1, 2, 3, 4, 5]
```
