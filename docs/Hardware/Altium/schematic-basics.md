After [setting up your project](../../Hardware/Altium/project-setup.md), you can begin designing the schematic. This acts as a blueprint of the circuit. Once it's created and validated, Altium can use it to populate and update the PCB with components.

---

## Adding Symbols

1. Choose a part from the [components library](../../Hardware/Altium/library.md).

2. Right-click on the part and select **Place**. If the component has multiple parts, you will have to choose one.

3. The symbol will appear translucent. Position it by hovering the mouse over the desired position and click to place. Right-click or ++esc++ to cancel. After placing the symbol, rotate it by selecting it and pressing ++space++.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/placing-component.png" alt="Placing Component"  style="max-width: 100%; height: auto;"/>
    </div>

4. Once placed, you can select the symbol and go to the **Properties** panel to access details.

## Annotating the Schematic

A component is labeled using a designator which can be edited in the **Properties** tab. The prefix (letter) is based on the type of part, and the number distinguishes it from other components of the same type.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/set-designator.png" alt="Setting Designator"  style="max-width: 100%; height: auto;"/>
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

Components in a schematic are connected together with a net. This can be indicated either by physically wiring them together or assigning a net label. 

### Wire

A wire can be drawn by right-click and select **Place → Wire**, or more easily, with ++ctrl+w++.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/select-wire.png" alt="Selecting Wire"  style="max-width: 100%; height: auto;"/>
</div>

Hover to position and click at the connecting pin to attach. Then click on the other component where it should connect. The wire adjusts when the component is moved.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/connecting-wire.png" alt="Connecting Wire"  style="max-width: 100%; height: auto;"/>
</div>

### Net

All connected components are part of the same net. In a schematic, you can indicate that a component is part of a particular net, even if it appears separate, by placing a net label.

Connect a short bit of wire to the desired pin. Then, similar to placing the wire, right-click and select **Place → Net Label**. This should be connected to the end of the wire, and the text edited to indicate which net it is a part of.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/net-label.png" alt="Net Label"  style="max-width: 100%; height: auto;"/>
</div>

### Port

A port makes a connection between multiple sheets of a schematic. The name of the port on one sheet corresponds to the name of the port on the other sheet to which it connects. It is placed the same way as a wire or net label.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/port-label-1.png" alt="Port Label on Sheet 1"  style="max-width: 50%; height: auto;"/>
</div>

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/port-label-2.png" alt="Port Label on Sheet 2"  style="max-width: 50%; height: auto;"/>
</div>

A power port specifically indicates a connection to a power or ground net.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/power-port-label.png" alt="Power Port Label"  style="max-width: 48%; height: auto;"/>
</div>

---

## Validation

Once the schematic is complete, it needs to be validated to check for any errors. Validation must be completed before generating the PCB layout.

To do this, go to **Project → Validate Project**.

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/validate-project.png" alt="Validate Project"  style="max-width: 100%; height: auto;"/>
</div>

Errors or warnings in the schematic design will appear in the **Messages** panel. Some can be ignored, but others indicate issues that need to be resolved. In this example, a wire has been removed to demonstrate the resulting errors that must be corrected:

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/validate-project-warnings.png" alt="Validate Project Warnings"  style="max-width: 100%; height: auto;"/>
</div>