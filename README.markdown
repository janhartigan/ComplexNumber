# ComplexNumber

A JavaScript complex number class that allows you to do most of the core mathematical operations with complex numbers, including addition, subtraction, multiplication, and getting the modulus of a complex number.

<hr />

## properties

<pre>
/* The real part of the complex number
 * 
 * @type Number
 */
real: 0,

/* The imaginary part of the complex number
 * 
 * @type Number
 */
imaginary: 0,
</pre>

A complex number is made up of two parts: a real and an imaginary parts. In the complex number 3 + 5i, for example, the real part is 3 and the imaginary part 5.

Creating a ComplexNumber is done by passing in two parameters: 1) real part and 2) imaginary part:

<pre>
var complex = new ComplexNumber(3, 5);

complex.toString(); //returns "3 + 5i"
</pre>

## methods

The methods include mathematical operations (`add()`, `sub()`, `mult()`, `mod()`) and a `toString()` function that gives the string representation of the complex number (e.g. 3 + 5i)

### add

Adds two complex numbers together by adding the real parts and the complex parts.

<pre>
/**
 * The add operation which sums the real and complex parts separately
 * 
 * @param ==> 	If there is one argument, assume it's a ComplexNumber
 * 				If there are two arguments, assume the first is the real part and the second is the imaginary part
 * 
 * @return ComplexNumber
 */
add: function() {
    if(arguments.length == 1)
        return new ComplexNumber(this.real + arguments[0].real, this.imaginary + arguments[0].imaginary);
    else
        return new ComplexNumber(this.real + arguments[0], this.imaginary + arguments[1]);
},
</pre>

**Example usage**:

<pre>
var complex1 = new ComplexNumber(3, 5),
	complex2 = new ComplexNumber(1, 2),
	complexSum = complex1.add(complex2);

complexSum.toString(); //returns "4 + 7i"
</pre>

### sub

Subtracts a complex number from another by finding the difference between the real parts and the complex parts.

<pre>
/**
 * The subtract operation which subtracts the real and complex parts from one another separately
 * 
 * @param ==>   If there is one argument, assume it's a ComplexNumber
 * 			    If there are two arguments, assume the first is the real part and the second is the imaginary part
 * 
 * @return ComplexNumber
 */
sub: function() {
    if(arguments.length == 1)
        return new ComplexNumber(this.real - arguments[0].real, this.imaginary - arguments[0].imaginary);
    else
        return new ComplexNumber(this.real - arguments[0], this.imaginary - arguments[1]);
},
</pre>

**Example usage**:

<pre>
var complex1 = new ComplexNumber(3, 5),
	complex2 = new ComplexNumber(1, 2),
	complexDiff = complex1.sub(complex2);

complexDiff.toString(); //returns "2 + 3i"
</pre>

### mult

Multiplies a complex number with another. Given complex numbers A and B, the result of their multiplication is: [(realA * realB) - (imaginaryA * imaginaryB)] + [(realA * imaginaryB) + (imaginaryA * realB)]*i.

<pre>
/**
 * The multiplication operation which multiplies two complex numbers
 * 
 * @param ==> 	If there is one argument, assume it's a ComplexNumber
 * 				If there are two, assume the first is the real part and the second is the imaginary part
 * 
 * @return ComplexNumber
 */
mult: function() {
    var multiplier = arguments[0];

    if(arguments.length != 1)
        multiplier = new ComplexNumber(arguments[0], arguments[1]);

    return new ComplexNumber(this.real * multiplier.real - this.imaginary * multiplier.imaginary, 
							this.real * multiplier.imaginary + this.imaginary * multiplier.real);
},
</pre>

**Example usage**:

<pre>
var complex1 = new ComplexNumber(3, 5),
	complex2 = new ComplexNumber(1, 2),
	complexMult = complex1.mult(complex2);

complexMult.toString();
//returns "-7 + 11i" .... [(3 * 1) - (5 * 2)] + [(3 * 2) + (5 * 1)] * i  =  (3 - 10) + (6 + 5)i  =  -7 + 11i
</pre>

### mod

Returns the modulus of a complex number. The modulus is defined as the square root of the real part squared plus the imaginary part squared. This basically turns the complex number into a purely real number.

<pre>
/**
 * The modulus of a complex number
 * 
 * @return number
 */
mod: function() {
    return Math.sqrt(this.real * this.real + this.imaginary * this.imaginary);
},
</pre>

**Example usage**:

<pre>
var complex = new ComplexNumber(3, 4);

complex.mod(); //returns 5 (3^2=9 and 4^2=16. 9 + 16 = 25. Square root of 25 is 5. 
</pre>

### toString

Returns the string representation of a complex number (e.g. "3 + 5i")

<pre>
/**
 * The string representation of a complex number (i.e. 4 + 3i)
 * 
 * @return String
 */
toString: function() {
    return this.real + " + " + this.imaginary + "i";
}
</pre>

**Example usage**:

<pre>
var complex = new ComplexNumber(3, 4);

complex.toString(); //returns "3 + 4i" 
</pre>