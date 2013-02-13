# smf-crate

A Clojure library designed to work with pallet to create an smf file.  It is specifically used with smartos but hopefully will work for other Solaris based OSes as well.  It is inspired by manifold.

## Continuous Integration Status
[![Build Status](https://travis-ci.org/rstradling/smf-crate.png)](https://travis-ci.org/rstradling/smf-crate])

## Usage
Artifacts are [released to Clojars](https://clojars.org/strad/smf-crate.  If you are using Maven, add the following definition to your `pom.xml`:
```xml
<repository>
 <id>clojuars.org</id>
 <url>http://clojars.org/repo</url>
</repository>
```

### The Most Recent Release
With Leiningen
   [org.clojars.strad/smf-crate "0.1.0"]

With Maven
   <dependency>
      <groupId>org.clojars.strad</groupId>
      <artifactId>monger</artifactId>
      <version>1.4.2</version>
   </dependency>

```clojure
  (def smf-data (create-smf "<category>" "<name of service>" "<version>" "run command" "user" "group"))
  (install-smf-service session smf-data "<remote location of smf file>" <true|false>) 
  ;; Please see the source code for options that can be passed in and overridden
  ;; Also note that the true or false parameter represents whether to remove the
  ;; temporary file on exit of the application or not.
```

To run the live-test sample you will need to do the following...
* Create a local smartos image where root can log in to it.
* Update your ~/pallet/config.clj to have the 
```clojure
{:datacenter {:provider "node-list"
	:node-list [["<machine-name>" "smartos-testing" "<ip address> :smartos]]
        }
}
```
run the tests by typing in 
```bash
lein with-profile live-test test :live-test
```
## License

Copyright © 2013 Ryan Stradling

Distributed under the Eclipse Public License, the same as Clojure.
