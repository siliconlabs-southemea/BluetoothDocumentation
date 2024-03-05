---
sort: 3
---

## Configure kit UART baudrate and handshake 

By default projects and developpement kits are set to 115200 bauds no handshake.
If you change that configuration in the VCOM instance of your project, then you need to modify the kit configuration.

  1.  In Simplicity Studio v5, go to the Launcher view and select your kit.

  2.  Then click right and select "Launch Console"

   <img src="./images/studio_2023-05-03_09-35-23.png" alt="" width="500" class="center">

  3.  In the console view, select Admin tab

   <img src="./images/studio_2023-05-03_09-38-38.png" alt="" width="900" class="center">

  4. to modify the kit UART settings and align it to your RCP settings use the following commands:

   ```sh
    serial vcom    
        --> will display your current settings
    
    serial vcom config speed 921600
        --> will configure the baudrate to 921600
        --> range is 9600-921600

    serial vcon config handshake rtscts
        --> will configure the handshake to rtscts
        --> options are rts/cts/rtscts/disable/auto
   ```

  5. Remark: to reset kit settings, you will need to type:

  ```sh
   serial vcom config speed 115200
   serial vcon config handshake auto
  ```

Once you have done all of the above, your RCP is ready to be used.