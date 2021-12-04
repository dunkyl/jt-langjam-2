# Main idea: just lots of pattern matching

 - Top level is a match on command line args
 - String/regular expr in matching. regex binding extensions, like python's ?P<>, can bind vars

## mostly automatically invertable functions for pattern matching
 - builtin functions manually implemented, like + and -, * and /, get and indexof, etc
 - user functions like maybe `addOnes: map (+ 1)` would expose a `addOnes⁻¹: map (- 1)`
 - then use in pattern on either side is allowed:
     `addOnes ([1,2,3,4]): x` then x is `[0,1,2,3] `
 - string interpolation
     `"the first x is {at(x, 0)}"` then it is `the first x is 0`
 - string deterpolation
     `"y is 5": "y is {y}"` then y is `"5"`
 - string mixerpolation
     `"y is 5?, then bind z to 6": "y is {y}?, then bind z to {z}"` -- incomplete match for case of str(y) was not "5"
 - inverse functions composed with string deterpolation
     `"b is 786 squared": "b is {sqrt(b)} squared"` think in english, reading the pattern on the right is true
     - another good reason for single-case matches
