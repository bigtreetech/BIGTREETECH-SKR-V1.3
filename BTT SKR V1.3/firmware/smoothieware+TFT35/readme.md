If you are using smootheware firmware, please disable the LEDs event in the configuration file,  as shown below
> leds_disable                        true

> play_led_disable                    true

![image](https://user-images.githubusercontent.com/38851044/96061203-337b5900-0ec5-11eb-9d09-7e546d5545cc.png)

Because there is no led on SKR V1.3, and the IO used by the LED on smoothieboard is of other use in SKR V1.3. If the LED is not disabled, other functions may be abnormal
