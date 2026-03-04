# Adding a simulated Sensor Driver

1) In _prj.conf_:  Enable Sensor Driver

       # Enable Sensor Driver
       CONFIG_SENSOR=y

2) Create _nRF54l15dk_nrf54l15_cpuapp_ overlay file. And add following lines:

       / {
           sensor_sim: sensor_sim{
           compatible = "nordic,sensor-sim";
           acc-signal = "wave";
           base-temperature = < 20 >;
           base-pressure = < 98 >;
           };
       };

3) in _main.c_ (just before <code>for (;;) {</code> line): Add initialization of simulated sensor:
   
	       #define SENSOR_NODE DT_NODELABEL(sensor_sim)
           const struct device *const dev = DEVICE_DT_GET(SENSOR_NODE);
           if (!device_is_ready(dev)) {
               printk("Sensor is not ready %s\n", dev->name);
               return 0;
           }
           printk("Sensor is ready!\n");

4) In _main.c_ (in <code>for (;;) {</code> loop): Call processing function

             process_sample(dev);

5) In _main.c_ (just after <code>#include <...></code> instructions): add processing function

       #include <zephyr/drivers/sensor.h>

       static void process_sample(const struct device *dev)
       {
           struct sensor_value pressure, temp;

           // Fetch a sample from the sensor and store it in an internal driver buffer
           if (sensor_sample_fetch(dev) < 0) {
               printk("Error: Sensor sample update error\n");
               return;
           }

           // Get a reading from a sensor device (read pressure)
           if (sensor_channel_get(dev, SENSOR_CHAN_PRESS, &pressure) < 0) {
               printk("Error: Cannot read LPS22HB pressure channel\n");
               return;
           }

           // Get a reading from a sensor device (read temperature)	
           if (sensor_channel_get(dev, SENSOR_CHAN_AMBIENT_TEMP, &temp) < 0) {
               printk("Error: Cannot read LPS22HB temperature channel\n");
               return;
           }

           /* display pressure */
           printk("pressure: %d.%d kPa, ", pressure.val1, pressure.val2);
           //printk("Pressure: %.1f kPa, ", sensor_value_to_double(&pressure));

           /* display temperature */
           printk("Temperature: %.1f C\n", sensor_value_to_double(&temp));
       }
   
