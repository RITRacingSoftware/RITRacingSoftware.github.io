After [setting up your project](../../Hardware/Altium/project-setup.md), you can begin designing the schematic. This serves as a blueprint of the, detailing every aspect of the circuit. Once it's created and validated, Altium can use it to populate and update the PCB with components.

---

## Adding Symbols

1. Choose a part from the [components library](../../Hardware/Altium/library.md).

2. Right-click on the part and select Place. If the component has multiple parts, you will have to choose one.

3. The symbol will appear translucent. Position by hovering the mouse and left-click to place or right-click/escape to cancel. It can be rotated after placing by selecting the symbol and pressing the spacebar.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/placing-component.png" alt="Fork Github Repository Image"  style="max-width: 100%; height: auto;"/>
    </div>

4. Once placed, you can select the symbol and go to the Properties panel to access details.

## Component Designators

A component is labeled using a designator which can be edited in the Properties tab. The prefix (letter) is determined by the type of part and the number sets it from other components of the same type in the circuit. 

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/set-designator.png" alt="Fork Github Repository Image"  style="max-width: 100%; height: auto;"/>
</div>

These are some common components:

- R - Resistor 
- C - Capacitor
- L - Inductor
- K - Relay
- Q - Transistor
- TP - Test Point
- U - Integrated Circuit

---

## Connecting Parts

Components in a schematic are connected together with a net. This can be indicated on a either by physically wiring them together or assigning a net label. 

### Wire

A wire can be drawn by right-click -> Place -> Wire, or more easily, with Ctrl-W.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/select-wire.png" alt="Select Wire"  style="max-width: 100%; height: auto;"/>
</div>

Hover to position and then click at the connecting pin to attach. Then you can click where on the other component you want it connected to. The wire adjusts when the component is moved.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/connecting-wire.png" alt="Connecting Wire"  style="max-width: 100%; height: auto;"/>
</div>

### Net

All connected components are part of the same net. In a schematic, you can indicate that a component is part of a particular net, even if it appears separate, by assigning a net label.

Connect a short bit of wire to the desired pin. Then, similar to placing the wire, right-click -> Place -> Net Label. This should be connected to the end of the wire, and the text edited to indicate which net it is a part of.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/net-label.png" alt="Net Label"  style="max-width: 100%; height: auto;"/>
</div>

### Port

A port makes a connection between multiple sheets of a schematic. The name of the port on one sheet corresonds to the name of the port on the other sheet to which it connects. It placed the same way as a wire or net label.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/port-label-1.png" alt="Port Label on Sheet 1"  style="max-width: 50%; height: auto;"/>
</div>

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/port-label-2.png" alt="Port Label on Sheet 2"  style="max-width: 50%; height: auto;"/>
</div>

A power port specifically indicates connection to a power or ground net. 

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/power-port-label.png" alt="Power Port Label"  style="max-width: 48%; height: auto;"/>
</div>

---

## Validation

Once the schematic is complete, it needs to be validated to ensure there are no errors. This must be done before the PCB layout. 

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/validate-project.png" alt="Validate Project"  style="max-width: 100%; height: auto;"/>
</div>

Errors or warnings in the schematic design will appear in the Messages panel. Some can be ignored, but others indicate issues that need to be resolved. In this example, a wire has been removed to demonstrate the resulting error that must be corrected:

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/validate-project-warnings.png" alt="Validate Project Warnings"  style="max-width: 100%; height: auto;"/>
</div>