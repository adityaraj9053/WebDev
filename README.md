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
<p><b> Syntax <b></p>
     
![image](https://github.com/user-attachments/assets/75060577-01c5-49da-8ea3-afbedbe601d8)
Ex:

     let numbers = [1, 2, 3, 4, 5];
     let max = Math.max(numbers);
command:

      console.log(max);
Output : 

      NaN
.Using spreading operator:

      let numbers = [1, 2, 3, 4, 5];
     let max = Math.max(...numbers);
command:

      console.log(max);
Output : 

       5
Ex- 2:

       function sum(x, y, z) {
          return x+y+z;
       }
       let numbers = [1, 2, 3];
 command:

      console.log(sum(...numbers)); // just expanding the argument
Output : 

      6    
### Rest parameter:
Allow a function to work with a variable no, of elements by bundling them into an array.

<b> spread <b> - expands an array into separate elements.
<b> rest <b> - bundles separate elements into an array.
Ex-

     const food1 = "pizza";
     const food2 = "Apple";
     const food3 = "CauliFlower";
     const food4 = "Spinach";
    const food5 = "Laddu";

    function openFridge(...foods) {
       console.log(foods);
    }
command:

      openFridge(food1)
Output : 

      ["pizza"]
command:

      openFridge(food1, food2)
Output : 

      ["pizza", "Apple"]

if you want not to show as an array, then:

     const food1 = "pizza";
     const food2 = "Apple";
     const food3 = "CauliFlower";
     const food4 = "Spinach";
    const food5 = "Laddu";

    function openFridge(...foods) {
       console.log(...foods);        // PACE 3 DOTS HERE ALSO
    }
command:

      openFridge(food1, food2, food5, food4, food3)
Output : 

      pizza Apple Laddu Spinach CauliFlower

If you don't want to give command in function rather then want to give command in console log:  

     const food1 = "pizza";
     const food2 = "Apple";
     const food3 = "CauliFlower";
     const food4 = "Spinach";
     const food5 = "Laddu";

    function openFridge(...foods) {
        return fods;
    }
    const kuchh = openFridge(food1, food2, food5, food4, food3);
command:

      console.log(kuchh);
Output : 

     ['pizza', 'Apple', 'Laddu', 'Spinach', 'CauliFlower']
