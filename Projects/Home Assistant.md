[Home Assistant](https://home-assistant.io) is an open-source, open-environment home automation platform.  While it can be installed on many platforms, the easiest (and likely most reliable) option is to run it on their pre-configured Raspberry Pi, the Home Assistant Yellow.

So as to not lock ourselves into any one manufacturer or standard, it is important to avoid smart home ecosystems that require dedicated hardware, such as Google Nest or Phillips Hue.  Open protocols such as Zigbee (and its nascent successor Matter) are preferred, but even these can be traps, as some walled ecosystems claim Zigbee compatibility, but it merely allows their base stations to intercommunicate, not to allow their products to be controlled by arbitrary base stations.

Home Assistant is flexible enough that it can operate multiple standards at once, making the Zigbee-to-Matter transition natural and transparent.

The primary use case will be to have control over the color temperature and luminance of the lighting in the house.  As such, it is imperative that we only buy bulbs with color-change ability, and dimmability is preferred.

Home Assistant's open environment means that other functionality can be take up if desired, such as setting up [[Pi-Hole]].
### Action Items
- Purchase Home Assistant Yellow unit
- Install HSY in understairs closet in a tidy manner
- Purchase and install light fixtures for the remainder of the house
- Purchase and install light bulbs for the remainder of the house
- Establish Zigbee network and connect all lights
- Ensure all lights are named appropriately
- Set up color temperature automation