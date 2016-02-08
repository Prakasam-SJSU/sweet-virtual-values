1. Compile Step
    1.1 Include macros in 'macros/index.js' overriding all operators with unary or binary function call.
    1.2 Resultant input file will have all operators replaced by unary or binary function calls.
    
    1.2 Include VProxy definition, essentially a wrapper over Proxy that contains a map to look up by key.
    1.3 Key being the underlying proxy and the value being a composite madeup of handler, original value, and classifier key.
    1.4 Unary/binary function calls verify is a operand is a VProxy and extract original value and calls left or right function of the proxy handler.
    1.5 Handler in turn performs invoked unray or binary function which will do the defalu op on the values.
    
2. Changes
    2.1 Don't include VProxy definition in the compile step
    2.2 So the source file being compiled doesn't have this appended to it and keeping it clear.
    
3. Implementing Taint
    3.1 Implement a function to taint any value.
    3.2 This function will return a VProxy with a specific classification key
    3.3 Also implement Unary and binary operations for the tainted values
    3.4 Compile it with vjs so the unary and binary ops delegate to unary and binary operators contained in VProxy.