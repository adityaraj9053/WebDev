# WebDev
## Java script:
### javascript proxy:

A Proxy is used to define custom behavior for fundamental operations (like reading, writing, deleting properties) on objects. It can be especially useful for things like logging, validation, or creating mock objects for testing.
It is like getter and setter but in modifying and polished way.

#### Proxies terminology
<b> Handler <b>
placeholder object which contains traps.

<b> Traps <b>
methods that provide property access.

<b> Target <b>
object which the proxy virtualizes.

#### Syntax:
     let proxy = new Proxy(target, handler);

#### Difference between proxy and getter setter
proxy:


    const staff = {
       name: "Ansh",
       age: 25
    }
    const handler = {
      get: (target, name) => {
        name in target ? console.log(target[name]): console.log('404 not found');
      },
      set: (target, name, value) => {
        target[name] = value;
      }
    }
    const staffProxy = new Proxy(staff, handler);
  On giving following command:
  
     staffProxy.position;
 It will show the 404 not error. 

 getter:
 
      const staff = {
         _name: "Ansh",
         _age: 25,

    get name() {
        console.log(this._name);
    },
    get age(){
        console.log(this._age);
    },
    set age(newAge) {
        this._age = newAge;
        console.log(this._age);
    }
};
staff.name;

