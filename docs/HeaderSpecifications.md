**Header Specifications**

1. API should accept one or more header-parameter(s) as method-attribute.
1. API should accept one or more header-parameter(s) as method-parameter.
    - API should accept these type of parameters' names differently from method-parameter's names.
1. API should accept header-parameter(s) as shared parameters through
     all request as interface attribute.
1. API should be able to pass all incoming headers - when we are in a http context - to 
    outgoing requests.