# REACT-LESSONS-INSTRUCTOR-ANDRES-R.-BUCHELI

## Take a look to the live example at:


## Usage:
* Accessing dynamic information with this.state.
* To make a component have state, give the component a state property. This property should be declared inside of a constructor method.
* this.state should be equal to an object.
* Using componentDidMount() to update a component.
* Use of the setInterval() function using the following syntax:
```
setInterval(() => {
      this.setState({ date: new Date() });
    }, oneSecond);
```

## Important:
Remember, the component lifecycle has three high-level parts:

* 1. Mounting, when the component is being initialized and put into the DOM for the first time
* 2. Updating, when the component updates as a result of changed state or changed props
* 3. Unmounting, when the component is being removed from the DOM

It’s certainly not in the unmounting phase—we don’t want to start our interval when the clock disappears from the screen! It’s also probably not useful during the updating phase—we want the interval to start as soon as the clock appears, and we don’t want to wait for an update. It probably makes sense to stick this code somewhere in the mounting phase.

We’ve seen two functions: the render() and the constructor. Can we put this code in either of those places?

* render() isn’t a good candidate. For one, it executes during the mounting phase and the updating phase—too often for us. It’s also generally a bad idea to set up any kind of side-effect like this in render(), as it can create subtle bugs in the future.

* constructor() is also not great. It does only execute during the mounting phase, so that’s good, but you should generally avoid side-effects like this in constructors because it violates something called the Single Responsibility Principle. In short, it’s not a constructor’s responsibility to start side-effects. (You can read more about the principle on Wikipedia.)

If it’s not render() or the constructor, then where? Enter a new lifecycle method, componentDidMount().

componentDidMount() is the final method called during the mounting phase. The order is:

* The constructor
* render()
* componentDidMount()

In other words, it’s called after the component is rendered. This is where we’ll want to start our timer.
