I forked it purely to get it running on **Clojure 1.7.0** and upgraded to the lastest versions all the dependencies.

# clj-soap

clj-soap is SOAP server and client using Apache Axis2.


## Usage

### Client

You can call remote SOAP method as following:
```clojure
(require '[clj-soap.core :as soap])

(let [client (soap/client-fn "http://www.webservicex.com/globalweather.asmx?WSDL")]
   (client :GetWeather "Murcia" "Spain" ))

```
### Server

To make SOAP service:
```clojure
(require '[clj-soap.core :as soap])

;; Defining service class
(soap/defservice my.some.SoapClass
  (someMethod ^String [^Integer x ^String s]
              (str "x is " x "\ts is " s)))

;; Start SOAP Service
(serve "my.some.SoapClass")
```
`defservice` needs to be AOT-compiled.
For example, `lein compile` before running server.

#### Type Hint

SOAP services need typehints.
`String` for arguments and `void` for return value,
if you don't specify typehints.

## License

Copyright (C) 2011 Tetsuya Takatsuru

Distributed under the Eclipse Public License, the same as Clojure.

