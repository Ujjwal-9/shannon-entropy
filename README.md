# shannon-entropy
implementation of shannon entropy

code:
```javascript
function(shannon) {
'use strict';

  // Create a dictionary of character frequencies and iterate over it.
  function process(s, evaluator) {
    var h = Object.create(null), k;
    s.split('').forEach(function(c) {
      h[c] && h[c]++ || (h[c] = 1); });
    if (evaluator) for (k in h) evaluator(k, h[k]);
    return h;
  };
  
  // Measure the entropy of a string in bits per symbol.
  shannon.entropy = function(s) {
    var sum = 0,len = s.length;
    process(s, function(k, f) {
      var p = f/len;
      sum -= p * Math.log(p) / Math.log(2);
    });
    return sum;
  };
  
  // Measure the entropy of a string in total bits.
  shannon.bits = function(s) {
    return shannon.entropy(s) * s.length;
  };
  
  // Log the entropy of a string to the console.
  shannon.log = function(s) {
    console.log('Entropy of "' + s + '" in bits per symbol:', shannon.entropy(s));
  };
})(window.shannon = window.shannon || Object.create(null)
```
