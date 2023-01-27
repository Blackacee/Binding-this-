# Binding-this-

var monitor = {
 threshold: 5,
 check: function(value) {
 if (value > this.threshold) {
 this.display("Value is too high!");
 }
 },
 display(message) {
 alert(message);
 }
};
monitor.check(7); // The value of `this` is implied by the method call syntax.
var badCheck = monitor.check;
badCheck(15); // The value of `this` is window object and this.threshold is undefined, so value >
this.threshold is false
var check = monitor.check.bind(monitor);
check(15); // This value of `this` was explicitly bound, the function works.
var check8 = monitor.check.bind(monitor, 8);
check8(); // We also bound the argument to `8` here. It can't be re-specified.
