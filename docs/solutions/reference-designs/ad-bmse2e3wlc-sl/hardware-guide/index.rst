.. _ad-bmse2e3wlc-sl hardware:

Hardware Guide
==============

Components and Connections
--------------------------

..  figure:: baseboard-components.png
    :width: 800 px

    AD-BMSE2E3WLC-48V Baseboard Components

+-------+---------------+---------------------------------------------+
| No.   | Component     | Function                                    |
+=======+===============+=============================================+
| 1     | Battery Cell  | Connector going to battery cells            |
|       | Connector     |                                             |
+-------+---------------+---------------------------------------------+
| 2     | ADBMS1816W    | Battery Cell monitoring IC                  |
+-------+---------------+---------------------------------------------+
| 3     | LTC7000       | FET Driver IC                               |
+-------+---------------+---------------------------------------------+
| 4     | 12V Supply    | 12V supply access                           |
+-------+---------------+---------------------------------------------+
| 5a    | Rsense_N      | Resistor sensing for detecting and          |
|       |               | monitoring total current on the baseboard   |
|       |               | negative side                               |
+-------+---------------+---------------------------------------------+
| 5b    | Rsense_P      | Resistor sensing for detecting and          |
|       |               | monitoring total current on the baseboard   |
|       |               | positive side                               |
+-------+---------------+---------------------------------------------+
| 6a    | Arduino       | Arduino Header Connector left side          |
|       | Headers       |                                             |
+-------+---------------+---------------------------------------------+
| 6b    | Arduino       | Arduino Header Connector right side         |
|       | Headers       |                                             |
+-------+---------------+---------------------------------------------+
| 7     | Featherwing   | Connector for placing Featherwing form-     |
|       | Connector     | factor boards                               |
+-------+---------------+---------------------------------------------+
| 8     | VBAT+         | Positive Terminal Connector for total       |
|       | Connector     | voltage capacity of the battery pack        |
+-------+---------------+---------------------------------------------+
| 9     | isoSPI        | Duraclik isoSPI connector terminals         |
|       | Connectors    |                                             |
+-------+---------------+---------------------------------------------+
| 10    | ADG701        | 5V switch USB enabled                       |
+-------+---------------+---------------------------------------------+
| 11    | LTC7138       | 5V Analog and 5V digital LDO Regulator      |
+-------+---------------+---------------------------------------------+
| 12    | V+ Output     | Output control connector from V+ going to   |
|       | Control       | Link+ Output                                |
|       | Connector     |                                             |
+-------+---------------+---------------------------------------------+
| 13    | LINK+_OUT     | Access going to load side                   |
+-------+---------------+---------------------------------------------+
| 14    | Common GND    | Access ground going to load side            |
+-------+---------------+---------------------------------------------+

.. figure:: daughterboard-components.png
    :width: 600 px

    AD-BMSE2E3WLC-48V Daughter Board Components

+-----+----------------------+-----------------------------------------+
| No. | Component            | Function                                |
+=====+======================+=========================================+
| 1   | Eval board Cell      | eval-adbms1816wlc connector             |
|     | Connector            |                                         |
+-----+---------------------+------------------------------------------+
| 2   | Eval board           | eval-adbms1816wlc 16-Cell Monitoring    |
|     |  ADBMS1816W (U3)     | Chip                                    |
+-----+----------------------+-----------------------------------------+
| 3a  | Eval board Arduino   | Arduino Header Connector left side      |
|     | Headers              |                                         |
+-----+----------------------+-----------------------------------------+
| 3b  | Eval board Arduino   | Arduino Header Connector right side     |
|     | Headers              |                                         |
+-----+----------------------+-----------------------------------------+
| 4   | Eval board isoSPI    | Duraclik isoSPI for connector terminals |
|     | Connectors           | for eval-adbms1816wlc                   |
+-----+----------------------+-----------------------------------------+

Test Points
-----------

**AD-BMSE2E3WLC-48V Baseboard**

.. figure:: baseboard-testpoints.png
    :width: 600 px

    AD-BMSE2E3WLC-48V Baseboard Test Points

+----------------+------------------+-----------------+---------------+
| Test Point     | Name             | Typical (V)     | Range (V)     |
+================+==================+=================+===============+
| TP6            | PORT             | 4.9             | 4.5  to 5.15  |
+----------------+------------------+-----------------+---------------+
| TP8            | TRANS            | 0               | 0             |
+----------------+------------------+-----------------+---------------+
| TP7            | VREG             | 4.9             | 4.7 to 5.15   |
+----------------+------------------+-----------------+---------------+
| 12V            | 12V SUPPLY       | 11.9            | 11.5 to 12.5  |
+----------------+------------------+-----------------+---------------+
| E1 (PIN2)      | 5V_ANA           | 5               | 4.5 to 5.15   |
+----------------+------------------+-----------------+---------------+
| E2 (PIN2)      | 5V_DIG           | 5               | 4.5 to 5.15   |
+----------------+------------------+-----------------+---------------+

Hardware Setup
--------------

**Requirements**

Required Hardware
-----------------

* 1 × AD-BMSE2E3WLC-48V Baseboard
* 1 × EVAL-ADBMS1816WLC Daughter Board
* 2 × DC2472A Battery Emulator
* 1 × MAX32666FTHR Microcontroller
* 1 × MAX32625PICO Programming Board
* 2 × isoSPI twisted-pair cables
* 1 × 10-pin SWD debugger cable
* 3 × Micro-USB to USB cables
* 1 × PC/Laptop
* 2 × Red Alligator-to-Banana Plug Cables (1166-12-0)
* 2 × Black Alligator-to-Banana Plug Cables (1166-12-0)
* 12 × Pin Header Shunts (if not yet installed)

Jumper Configuration
~~~~~~~~~~~~~~~~~~~~

**AD-BMSE2E3WLC-48V Baseboard**

From the list of required hardware, select the **AD-BMSE2E3WLC-48V Baseboard**.

Install the shunt connectors (if not yet installed) and ensure correct
positions, as highlighted in red in the figure below.

.. important:: 

    Header P16 must be configured with the shunt installed between
    pin 2 and pin 3. This setting configures the board for 48V operation.

.. figure:: baseboard-shunt-config.png
    :width: 1500 px

    AD-BMSE2E3WLC-48V Baseboard Shunt Configuration

----

**EVAL-ADBMSE2E3WLC Daughter Board**

Ensure that the shunt connectors are properly configured for **P17, P24,
P34, P30, P18, and P35.**

.. figure:: daughterboard-shunt-config.png
    :width: 700 px

    EVAL-ADBMSE2E3WLC Daughter Board Shunt Configuration

Battery Emulator Setup
~~~~~~~~~~~~~~~~~~~~~~

.. note:: 
    The DC2472A Battery Emulator Board is used for cell voltage
    input in this setup.

-   Plug the screw-terminal block into the cell voltage connector of the
    two DC2472A battery emulators.

-   Connect the first DC2472A battery emulator to the AD-BMSE2E3WLC-48V
    Baseboard through the cell connector.

    .. figure:: baseboard-to-emulator.png
        :width: 600 px

        AD-BMSE2E3WLC-48V to Battery Emulator Setup

-   Connect the second DC2472A battery emulator to the EVAL-ADBMS1816WLC
    Daughter Board through the cell connector.

    .. figure:: daughterboard-to-emulator.png
        :width: 600 px

        EVAL-ADBMS1816WLC to Battery Emulator Setup

-   Connect a 5V external power source to the DC2472A (J1) using a USB
    cable. External power supply is recommended for adequate power.

-   Alternatively, power it through a PC using a USB cable.

**Power Verification**

After powering up:

-   On **DC2472A**:

    - Blue LED (LED1) should turn **ON**

        .. figure:: emulator-led-on.png
            :width: 350 px

            DC2472A Emulator Power LED

-   On **AD-BMSE2E3WLC-48V Baseboard**:

    - Red LED (DS3) and Green LED (DS1) should turn **ON**

        .. figure:: baseboard-led-on.png
            :width: 600 px

            AD-BMSE2E3WLC-48V Baseboard Power LED

Microcontroller Connection
~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Attach the MAX32666FTHR microcontroller to the AD-BMSE2E3WLC-48V 
    Baseboard through the Featherwing connector.

    .. figure:: max32666fthr-connection.png
        :width: 600 px

        MAX32666FTHR to AD-BMSE2E3WLC-48V Baseboard

48V Connection
~~~~~~~~~~~~~~

-   Connect the red alligator to banana jack cable between **48V** and
    **TP11** on the AD-BMSE2E3WLC-48VV as shown below.

    .. figure:: 48V-connection.png

        48V Connection

Cable and PC Connection
~~~~~~~~~~~~~~~~~~~~~~~

A. Plug the micro-USB cable to the first DC2472A battery emulator
   that is connected to AD-BMSE2E3WLC-48V.

B. Plug the micro-USB cable to the second DC2472A battery emulator
   that is connected to EVAL-ADBMS1816WLC.

C. Plug the micro-USB cable into the MAX32666FTHR.

D. Connect the 2-wire isoSPI cable from P10 of AD-BMSE2E3WLC-48V.

E. Connect the other end of the 2-wire isoSPI cable to P10 of
   EVAL-ADBMS1816WLC.

F. Connect all USB cables to a USB hub (preferred). 

.. note:: 
    If your PC/laptop USB ports can supply ≥1 A, you may connect devices 
    directly without a USB hub.

Your setup should look like below:

.. figure:: full-integration-setup.png
    :width: 600 px

    AD-BMSE2E3WLC-48V Full Hardware Evaluation Setup

|

The AD-BMSE2E3WLC-SL comes complete with firmware and easy-to-use application GUI. 
Access the software resources and see the setup procedure in the 
:ref:`AD-BMSE2E3WLC-SL Software User Guide <ad-bmse2e3wlc-sl software>`.
