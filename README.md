# FFE-CCS
Data for integrating the later model EVCC module (GFM2) with an earlier model Focus Electric

The primary differences between the older model Focus Electric without CCS and the later models with, are as follows:

CCS port in place of the original J1772 port, updated cover/ring/fender to fit it
"Generic Function Module 2" installed between the DC pins and HV harness and looped into the pilot line
Updated HV harness to support the new DC connection through the GFM2 and continuation of the HV interlock circuit from the PTC heater

Provided one has a means to tap into the HV bus, the updated hardness is not strictly required. Inside the EVCC, the battery and "ICS" connections are hard linked and always connected, making the connection by the charging lines a switched tap that could exist almost anywhere in the bus - similar to the TCU hard wire used by the FFE-CHAdeMO project.

With this HV DC connection taken care of, the rest of the connections are straight forward. The existing pilot line would need to be run through the EVCC before continuing to the SOBDM as normal. The EVCC would need to be tapped into the HSCAN bus, power and ground. From there PT1000 thermistor connections would be made for the AC and DC plug zones, along with a dual polarity 12V latching solenoid with a sense line that reads 1k while open and 11k while closed.

For an older model focus the HV interlock lines could be added to those on the PTC heater loop but it is not strictly necessary for this to operate as an add on. The HV interlock contacts on the EVCC charger connection are monitored by the internal board and would need to be bridged to operate.

Operational Considerations

At this point communications with the rest of the vehicle are an unknown. It is enreitly possible that this module can pull data from other modules without any updates to their sw - though it is also possible that specific changes are needed in other systems to support this device.

Should updated SW be required to provide required CANBus data, a bridge may be used to create that traffic as needed and satisfy the EVCC data requirements. This should be possible to determine once it is wired in and CAN sniffed.
