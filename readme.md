#Javascript Quiz - Sept 15


##Questions

1. Make a `Person` constructor with attributes: `name:string`, `height:string`, `age:number`, `sleeping:boolean`.

```
var Person = function (name, height, age) {
  this.name = name;
  this.height = height;
  this.age = age;
  this.sleeping = false;
};
```

2. Add prototype methods to `person`: `eat`, `sleep`, and `wakeUp`. (The `sleep` and `wakeUp` methods should toggle `sleeping` to `true/false`, and `eat` should return an eating noise.)

```
Person.prototype.eat = function() {
  return "nom nom nom";
};

Person.prototype.sleep = function() {
  if (this.sleeping === false) {
    this.sleeping = true;
  }
  else {
    return this.name + "is already sleeping!";
  }
};

Person.prototype.wakeUp = function() {
  if (this.sleeping === true) {
    this.sleeping = false;
  }
  else {
    return this.name + "is already awake!";
  }
};
```

3. Make a `Student` prototype that inherits from `person` and has the additional attribute of `studying:boolean`.

```
var Student = function (studying) {
  this.studying = false;
};

// classical inheritence
Student.prototype = new Person();
Student.prototype.constructor = Student;
```

4. Add methods to `Student` called `study`, and `stopStudy` to toggle `studying`

```
Student.prototype.study = function() {
  if (this.studying === false) {
    this.studying = true;
  }
  else {
    return this.name + "is already studying!";
  }
};

Student.prototype.stopStudy = function() {
  if (this.studying === true) {
    this.studying = false;
  }
  else {
    return this.name + "is not studying right now!";
  }
};
```

5. Override the `sleep` method on `student` to only run `sleep` if `studying` is `false`.

```
Student.prototype.sleep = function() {
  if (this.studying === false) {
    this.sleeping = true;
  }
  else {
    return this.name + "can't go to sleep while studying!";
  }
};
```
