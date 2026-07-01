.. _ad-bmse2e3wlc-sl software:

Software Guide
==============

This page provides the essential steps for firmware installation,
launching the GUI, establishing interface connections, and utilizing
various tabs for effective device evaluation.

Software Resources
------------------

.. admonition:: Download

    The following software is used for testing the AD-BMSE2E3WLC-SL:

    - :adi:`ACE Software <ace>`
    - AD-BMSE2E3WLC-SL GUI Firmware - **bms_measurement-max32665-iio-2x-adbms1816.hex**
    - AD-BMSE2E3WLC-SL ACE GUI Plugin Installer - **ADBMSE2E3WLC.1.2026.2041058-dev**
    - MAX32625PICO Image - **max32625_max32666fthr_if_crc_swd_v1.0.5**

Firmware Upload
---------------

**Step 1: Hardware Connection**

    - Connect the **10-pin SWD ribbon cable** to the MAX32666FTHR.
    - Connect the other end to the **MAX32625PICO.**
    - Connect the MAX32625PICO to your PC using a **micro-USB cable.**

**Step 2: Upload Firmware**

    - From the software package, locate the **MAX32625_PICO.bin** file.
    - Drag and drop it into the **MAINTENANCE** folder of the connected
      MAX32625PICO.
    - A progress bar indicates installation progress.

     .. figure:: max32625_pico_bin_upload.png

        Uploading MAX32625_PICO.bin file

    **Successful Installation Indicators:**

    - Device renames to **DAPLINK.**
    - A **MAX32666.HTM** file appears in the folder.

**Step 3: Upload Target Firmware**

    - Connect the MAX32625PICO to the MAX32666FTHR.
    - Ensure the MCU is powered via USB.
    - Drag and drop the **target firmware file** (from the software package) into the DAPLINK drive.

.. figure:: firmware-upload.png
    :width: 600 px

    Uploading Target Firmware

**Verification:**

    - The absence of a **FAIL.TXT** file in the DAPLINK folder indicates a successful upload.

----

GUI Setup
---------

**Step 1: Download Required Files**

    - Download the plugin package: **Board.ADBMSE2E3WLC ACEZIP.zip** (save locally)
    - Download the latest :adi:`ACE software <ace>` from Analog Devices.

    .. figure:: ace-software-download.png

        ACE Software Download

**Step 2: Install ACE Software**

    - Run the installer.
    - Follow on-screen installation steps, as shown in the following
      figures:

    .. figure:: ace-software-installation.png
    
        ACE Software Installation Steps

    - Verify installation via the Start Menu.

    .. figure:: ace-on-start-menu.png
       :align: center

       ACE Software Start Menu Verification

**Step 3: Load Plugin**

    - Run the downloaded ``ACEZIP file``.

    - Accept the prompt warning about unapproved EULA plugins.

    .. figure:: plugin-TOU.png
       :width: 500 px

    - Continue to load the plugin.

   .. figure:: ACEZIP-file.png

        BMSE2E3WLC-SL Plugin

Launching and Configuring the GUI
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    - Power up the hardware setup again (connect all USB cables to the PC or to a USB hub).

    - Launch ACE and **double-click the plugin**.

    - Open **Settings** (highlighted in GUI).

    .. figure:: ACE-homepage.png

        ACE GUI Homepage

**Configure Serial Communication**

    - Open **Device Manager** and note the **COM port number**.

    .. figure:: device-manager-comport.png

       Device Manager COM Port Detection

In ACE:

1. Go to **Settings → Serial Ports** and add the detected COM port.

2. Set **Protocol = IIO**, then ``Enable`` the port.

3. Click ``OK``.

    .. figure:: ace-serial-ports-config.png

       ACE Serial Port Settings

4. Restart ACE.

   Expected Result: Plugin **AD-BMSE2E3WLC-48V** appears.

----

GUI Overview
~~~~~~~~~~~~

The AD-BMSE2E3WLC-SL GUI provides real-time monitoring of
battery-pack parameters, cell voltages, current measurements,
operating state, and temperature information. The dashboard is
designed to provide a quick overview of battery health and
system status during evaluation and testing.

.. figure:: AD-BMSE2E3WLC-SL_GUI.png

    AD-BMSE2E3WLC-SL GUI

Main Dashboard Layout
+++++++++++++++++++++

The GUI is divided into three primary sections:

1. System Status Indicators (Top Middle Section)
2. Vehicle State and Temperature Monitoring (Top Right Section)
3. Individual Cell Voltage Monitoring (Bottom Section)

Stack Voltage Gauge
+++++++++++++++++++

The **Stack Voltage** gauge displays the total voltage of the
battery pack.

    Purpose

    * Monitors overall pack voltage.
    * Confirms proper connectivity of all battery cells.
    * Verifies battery charging and discharging behavior.

    Displayed Information:

    * Real-time pack voltage value.
    * Green indicator showing normal operation.
    * Gauge range covering the supported battery stack voltage.

    Example

    * Displayed value: **86.70V**

**Module Current Gauge**

The **Module Current** gauge displays the instantaneous battery
current.

    Purpose

    * Indicates whether the battery is charging or discharging.
    * Monitors load current and charging current.

    Current Direction

    * Positive (+) Current: Charging
    * Negative (-) Current: Discharging

    Example

    * Displayed value: **-1.95A**
    * Indicates the battery is supplying current to a load.

**Max Charge Current Gauge**

The **Max Charge Current** gauge displays the allowable charging
current configured by the BMS.

    Purpose

    * Indicates the maximum current permitted during charging.
    * May be limited by battery conditions, temperature, or safety
      requirements.

    Monitoring Use

    * Verify charging limits before connecting a charger.
    * Validate BMS protection settings.

    Example

    * Displayed value: **0A**

**Max Discharge Current Gauge**

The **Max Discharge Current** gauge displays the allowable
discharge current.

    Purpose

    * Indicates the maximum current available to the load.
    * Helps validate discharge protection behavior.

    Monitoring Use

    * Verify discharge capability during driving conditions.
    * Observe current-limit changes caused by faults or temperature
      restrictions.

    Example

    * Displayed value: **1.95A**

Vehicle State Selection
+++++++++++++++++++++++

The **Vehicle State** panel allows the user to select and
monitor the current operating mode.

Available States:

+----------+--------------------------------------------------+
| State    | Description                                      |
+==========+==================================================+
| Parked   | Low-activity mode; output path disabled or       |
|          | limited.                                         |
+----------+--------------------------------------------------+
| Driving  | Vehicle is actively supplying power to the load. |
+----------+--------------------------------------------------+
| Charging | Battery is connected to a charging source.       |
+----------+--------------------------------------------------+
| Fault    | System enters protection mode due to an          |
|          | abnormal condition.                              |
+----------+--------------------------------------------------+

Purpose

Vehicle states control the behavior of the BMS and allow users
to evaluate operating-state transitions during system testing.

Temperature Sensors
+++++++++++++++++++

The **Temperature Sensors** section displays temperature
measurements from connected thermistors.

    Displayed Information

    * BMS 1 temperature channels
    * BMS 2 temperature channels

    Purpose

    * Monitor battery-pack temperature.
    * Verify thermistor operation.
    * Evaluate thermal protection functionality.

    Typical Applications

    * Overtemperature testing
    * Thermal characterization

Cell Voltage Monitoring
+++++++++++++++++++++++

The lower section of the GUI displays individual cell voltages
for each monitored battery cell.

    **BMS 1 Cell Monitor**

    * Cells 1 to 16
    * Individual voltage readings
    * Battery charge indicators

    **BMS 2 Cell Monitor**

    * Cells 1 to 16
    * Individual voltage readings
    * Battery charge indicators

Visual Indicators
+++++++++++++++++

+------------------------+--------------------------------------+
| Indicator              | Meaning                              |
+========================+======================================+
| Green Check Mark       | Parameter or cell voltage is within  |
|                        | the normal operating range.          |
+------------------------+--------------------------------------+
| Battery Icon           | Visual representation of the cell    |
|                        | level or status.                     |
+------------------------+--------------------------------------+
| Green Battery Level    | Cell voltage is present and measured |
|                        | successfully.                        |
+------------------------+--------------------------------------+
| Voltage Reading        | Actual measured cell voltage value.  |
+------------------------+--------------------------------------+
| Gauge Pointer in Green | Measurement is within expected       |
| Region                 | operating limits.                    |
+------------------------+--------------------------------------+
| Fault State Selected   | Protective action is active or a     |
|                        | fault condition has been detected.   |
+------------------------+--------------------------------------+

The dashboard serves as the primary real-time monitoring
interface for validating pack voltage, current flow, cell
voltages, temperatures, and operating-state transitions during
AD-BMSE2E3WLC-SL evaluation.

Functional Testing Using GUI
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Voltage Adjustment Test
+++++++++++++++++++++++

**Minimum Voltage Test**

1. Rotate both DC2472A knobs **clockwise (for minimum setting)**

2. Expected readings:

     - Cell voltage: **1.3V to 1.7V**

     - Stack voltage: decreases

    .. figure:: minimum-voltage-test.png
       
       AD-BMSE2E3WLC-SL Minimum Voltage Test

**Maximum Voltage Test**

1. Rotate both DC2472A knobs **counterclockwise (for maximum setting)**
2. Expected readings:

    - Cell voltage: **4.0V to 5.0V**

    - Stack voltage: increases

    .. figure:: maximum-voltage-test.png

        AD-BMSE2E3WLC-SL Maximum Voltage Test

   You may adjust one emulator at a time to observe changes clearly.

----

Output Power Delivery Test
+++++++++++++++++++++++++++

Measure using a **Digital Multimeter (DMM)**:

    - Connect **DMM (–)** to **Ground**.
    - Connect **DMM (+)** to **TP23**.

   Expected reading: **4.0V to 4.7V**

   Notice that output “Stack Voltage” is at **94.43V** while the DMM reading is at **4.3V.**

In GUI:

    - Set **Vehicle State = Driving**.
    - Verify voltage again.

    .. figure:: driving-mode-pd.png

       AD-BMSE2E3WLC-SL Power Delivery Test "Driving" Mode
 
    **Vehicle State = Parked**

    .. figure:: parked-mode-pd.png
       
       AD-BMSE2E3WLC-SL Power Delivery Test "Parked" Mode     

**Shutdown Procedure**

Follow this sequence to safely power down:

1. Disconnect power from MAX32666FTHR microcontroller.
2. Disconnect power from both DC2472A battery cell emulators.
3. Remove all cables.
4. Return hardware to proper storage.
