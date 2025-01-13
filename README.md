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
        name in target ? console.log(target[name]): console.log('404 not found');  // means if name is given then, 
      },
      set: (target, name, value) => {
        target[name] = value;
      }
    }
    const staffProxy = new Proxy(staff, handler);
On giving following command:

    staffProxy.name;
It will  show:

    Ansh
On giving following command:
  
     staffProxy.position;  
 It will show: 
 
     404 not found 
___________________________________________________________________________________________________________________
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
On giving following command:

    staff.position;
it will show:

    undefined

Clearly, we can see with the help of proxy we had set the well-defined custom behaviour i.e. " any value other than previous seted, give "404, error".

### Generators:
function which can be exited and later re-entered. Their context will be saved across re-entrances.

    function* numbGen() {
      yield 1;
      yield 25;
      yield 3;
      yield 4;
    }
    const gen = numbGen();
output:

    console.log(gen.next());
    {value: 1, done: false}
    value: 25, done: false}
    value: 3, done: false}
    value: 4, done: false}
    value: undefined, done: true}

if: console.log(gen.next().value);

    1
    2
    3
    4
    undefined

Basically, it is used to generate numbers. Ex- if we want to print 1 billion nummbers, then, firstly we have to store that numbers then, print. It will take lots of space. <b> other way is to use Generators <b>.

    function* numbGen() {
     i = 0;
    while(true){
        yield i++;
    }
    }
    const gen = numbGen();
    console.log(gen.next().value);
     1
     2
     3
     4
     5
     6
     7
     8

### Spreading property:
It allows an iterable such as an array or string to be expanded into separate elements. (unpacks the elements)
<b> Syntax <b>
<b> For function call <b> 
