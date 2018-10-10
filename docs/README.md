[Back to Main Page](https://danielbortfeld.github.io/)

<a name="Dynamic_Delegate"/>

# Dynamic Delegate (C++)

Define a **dynamic delegate** like in the Unreal framework, but without using the Unreal framework! The delegate can be subscribed by a pair of a YourBaseClass\* and a function to call on the base class. Broadcast() will call the functions on the respective objects.
**You will find the useage below and the source code in the [repository](https://github.com/DanielBortfeld/DanielBortfeld.github.io/blob/master/Composition/Delegate.h)**.    
### [View Delegate Source Code on GitHub](https://github.com/DanielBortfeld/DanielBortfeld.github.io/blob/master/Composition/Delegate.h)

```c++
// (c) Daniel Bortfeld 2016 - 2017

// GameObject.cpp

void GameObject::Destroy()
{
	std::cout << Name << " was destroyed" << std::endl;
	delete this;
}

// Main.cpp

#include "Delegate.h"

DECLARE_DELEGATE(DestroyDelegate)

int main()
{
	DestroyDelegate Destroy;
    
	GameObject* gameObject2 = new GameObject("GO 1");
	GameObject* gameObject3 = new GameObject("GO 2");
	GameObject* gameObject4 = new GameObject("GO 3");
    
    printf_s("Adding function GameObject::Destroy of GO 1, 2 & 3 to delegate Destroy...\n");
	Destroy.Add<GameObject>(gameObject2, &GameObject::Destroy);
	Destroy.Add<GameObject>(gameObject3, &GameObject::Destroy);
	Destroy.Add<GameObject>(gameObject4, &GameObject::Destroy);
    
    // ...
    
    printf_s("Broadcasting delegate Destroy...\n");
	Destroy.Broadcast();
    
    return 0;
```

### Output

Adding function GameObject::Destroy of GO 1, 2 & 3 to delegate Destroy...    
Broadcasting delegate Destroy...    
GO 1 was destroyed    
GO 2 was destroyed    
GO 3 was destroyed    

***    

Further examples:   

* [Etos Videos](https://DanielBortfeld.github.io/Etos/)    
* [CollisionManager for the MonoGame-Framework (C#)](https://DanielBortfeld.github.io/Collision/)    
* [Pathfinding in the Console (C++)](https://DanielBortfeld.github.io/Console-Pathfinding/)    

***    

[Back to Main Page](https://DanielBortfeld.github.io/)   
