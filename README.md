## Summary

This repo contains the annotations used by the [BuzzFuzz Engine](https://github.com/johnnyrockett/JavaFuzzer).

These annotations let BuzzFuzz know which methods you want to fuzz test along with how you want those tests to be constrained.

## Example

* To mark a method for the BuzzFuzz engine to test, simply add the ` @Fuzz ` annotation before the message.

* Constraints can also be added to the fuzz tests by using the ` @FuzzConstraint ` annotation. This annotation can specify constraints in the following ways:
    * config file: configFile = "fuzzConfig.xml"
    * objectPath: objectPath = "Object"
    * lowerBound: lowerBound = 0
    * upperBound: upperBound = 100

Ultimately, an example of these annotations being used would look like this:

```java
@Fuzz
@FuzzConstraint(lowerBound = 0, upperBond = 100)
@FuzzConstraint(configFile = "fuzzConfig.xml", objectPath = "")
public static RadarChart newRadarChart(final List<? extends Plot> plots) {
    return new RadarChart(Plots.copyOf(plots));
}
```