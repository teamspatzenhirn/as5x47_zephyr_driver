# AS5X47 Zephyr Driver Module

## Usage

This is a west module. You can integrate it in your application by adding the project to your west manifest or by specifying it in your `EXTRA_ZEPHYR_MODULES`.

Enable the sensor by defining its location and properties in the devicetree (overlay).
For sensor configuration the `output-interface` (`abi` or `uvw`) and `uvw-polepairs` (1-7) devicetree settings are provided.

```c
&lpspi4 {
    my_sensor: as5x47@0 {
        compatible = "ams,as5x47";
        output-interface = "uvw";
        uvw-polepairs = <7>;
        spi-max-frequency = <1000000>;
        status = "okay";
        reg = <0>;
    };
};
```
## Example

A full working example for reading sensor values on a Teensy 4.1 can be found [here](samples/sensor/as5x47/).

## Writing Out-Of-Tree Drivers

Since this was kind of a pain to figure out, here are a few helpful links if you want to do this:

* https://interrupt.memfault.com/blog/building-drivers-on-zephyr
* https://blog.golioth.io/adding-an-out-of-tree-sensor-driver-to-zephyr/
* https://jonasotto.com/posts/zephyr_out_of_tree_driver/
