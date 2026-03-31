# KCONFIG: Adding Zephyr Logging

1) First, we add the Zephyr Logging software module to our project. To do this, we copy the following KCONFIG definition into the _prj.conf_ file.

       # Enable Logging
       CONFIG_LOG=y


2) In __main.c__ file add following lines after the <code>#include <...></code> instructions.

       #include <zephyr/logging/log.h>

       /* LOG MODULE REGISTRATION */
       LOG_MODULE_REGISTER(MyApp,LOG_LEVEL_INF);

  __Note:__ <code>LOG_MODULE_REGISTER()</code> macro has two parameters: <br>
  >  - first parameter: module name <br>
  >   - second parameter (optional): log level (see following table)

| pre-define parameter | description   |  Log Messages that will be shown   |
|----------------------|---------------|------------------------------------|
|  LOG_LEVEL_NONE      |   off         |   no logging                       |  
|  LOG_LEVEL_ERR       |   ERROR       |  only <code>LOG_ERR()</code> messages will be shown |
|  LOG_LEVEL_WRN       |  WARNING      |  <code>LOG_WRN()</code> and <code>LOG_ERR()</code> messages will be shown |
|  LOG_LEVEL_INF       |  INFO         |  <code>LOG_INF()</code>, <code>LOG_WRN()</code> and <code>LOG_ERR()</code> messages will be shown |
|  LOG_LEVEL_DBG       |  DEBUG        |  <code>LOG_DBG()</code>, <code>LOG_INF()</code>, <code>LOG_WRN()</code> and <code>LOG_ERR()</code> messages will be shown |


3) Let's use Logging instead of the <code>printf()</code> instruction. Replace the line <code>printf("LED state: %s\n", led_state ? "ON" : "OFF");</code> by the following one:

       LOG_INF("LED state: %s", led_state ? "ON" : "OFF");
   
