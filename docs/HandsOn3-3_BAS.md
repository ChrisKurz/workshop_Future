# nPM2100 + Bluetooth: Adding standard BLE Battery Service (BAS)

1) add to _prj.conf_: enable BT BAS Service

       # Enable Battery Service (BAS) Bluetooth profile
       CONFIG_BT_BAS=y

2) add to _main.c_

       #include <zephyr/bluetooth/services/bas.h>

3) Update/set the BAS Service characteristic for the battery Level. This could be done inside of _fuel_gauge_update()_ for example, with (float) soc being the state of charge, returned from the FG algorithm

       bt_bas_set_battery_level((uint8_t)soc);
      
