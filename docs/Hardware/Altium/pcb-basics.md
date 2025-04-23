After creating the [schematic](../../Hardware/Altium/schematic-basics.md), you can move on to designing the PCB. There are many factors that contribute to a good PCB design -- minimizing noise, ensuring good connections, and balancing performance with reliability. To start with, however, you should look to keep it simple and organized.

---

## Setup

1. When laying out the PCB, first ensure that the completed schematic has been [validated](../../Hardware/Altium/schematic-basics.md/#validation) as necessary.
2. If you haven't done so already, you should [add a PCB document to the project](../../Hardware/Altium/project-setup.md).

## Layers

### The Stackup

A PCB contains multiple layers, each of which serves a different purpose. The configuration of these layers is knows as the "stackup". The team's PCBs often uses 4 layers:

- Top Layer (Signal) – This is where the main routing and component placement is.

- Inner Layer 1 (Ground Plane) – A solid ground for signal return paths and EMI (electromagnetic interference) control.

- Inner Layer 2 (Power Plane) – Distributes power across the circuit (e.g., 5V, 3.3V).

- Bottom Layer (Signal) – For secondary routing or ground fill; also used for components in dense layouts.

That being said, some boards may require different stackups. This should be kept in mind before starting layout.


### Access and Edit Layers

1. To access the layer stack, navigate to Design -> Layer Stack Manager.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/access-layer-stack.png" alt="Access Layer Stack"  style="max-width: 100%; height: auto;"/>
    </div>

2. The default layer stack on Altium does not have the ground and power planes. Instead, it just has two signal layers (in yellow): 

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/default-layer-stack.png" alt="Default Layer Stack"  style="max-width: 100%; height: auto;"/>
    </div>

3. The configuration described earlier can be seen here in the New Member Board stackup. To create this, simply add and edit the required planes:

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/new-member-board-stackup.png" alt="New Member Board Layer Stack"  style="max-width: 100%; height: auto;"/>
    </div>

4. Once the layers have been set up, you can return to the main PCB document.


## Components

1. The schematic is used to initialize and update the components on the PCB. This can be done by selecting Design -> Update PCB Document at the top.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/update-pcb.png" alt="Update PCB"  style="max-width: 100%; height: auto;"/>
    </div>

2. A window will open with the list of components to be updated. The checkboxes on the left indicate whether or not a partciular component should be updated based on the schematic. By default, these should all be checked.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/execute-update-pcb.png" alt="Select Components and Execute Update PCB"  style="max-width: 100%; height: auto;"/>
    </div>

3. After confirming that everything is in order, you can proceed with executing the changes. The default footprints of each component will appear in an arbitary place on the schematic. These are connected with light lines indicating the net.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/updated-pcb-doc.png" alt="PCB Doc Updated with Components"  style="max-width: 100%; height: auto;"/>
    </div>

4. Bring the components onto the board by clicking and dragging them, and begin to lay them out. 

There are a number of things to keep in mind when coming up with a particular layout, but the general idea is that the component positioning should be logical, with the nets and routing in mind.


## Routing

There are a number of ways to route connections on a PCB:

- Trace
- Polygon pour
- Via (for connecting layers)

### Trace

A trace represents a wire -- the simplest connection between components. To draw a wire:

1. Select Interactive Routing from the toolbar. The short-cut for this is Ctrl-W (as with drawing a wire in the schematic).

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/interactive-routing.png" alt="Interactive Routing"  style="max-width: 60%; height: auto;"/>
    </div>

2. Click where you want to start your trace. If you start on a component, the trace will automatically set it's net to the component's.

3. Move your cursor to extend the trace and click again where you want the end point of that straight-line segment.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/trace.png" alt="Trace"  style="max-width: 60%; height: auto;"/>
    </div>

4. Press Esc to leave it there or continue by extending a second segment in the same way.


### Polygon Pour

A polygon pour is a solid copper object, which has greater surface area than a wire. This can be beneficial for a number of reasons (e.g. has lower impedence and more heat dissipation).

To draw a polygon pour:

1. Select Polygon Pour from the toolbar.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/toolbar-polygon-pour.png" alt="Polygon Pour in Toolbar"  style="max-width: 60%; height: auto;"/>
    </div>

2. Click where you want the starting vertex to be.
4. Press Shift+Spacebar to toggle between different corner angle modes.
3. Move your cursor to extend an edge and click again to create another vertex. You can create as many verticies as desired and press Backspace to remove the last vertex.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/polygon-pour.png" alt="Placing Polygon Pour"  style="max-width: 50%; height: auto;"/>
    </div>


5. Press Esc to complete the object.
6. To attach the polygon to a net, select the polygon and select it from the Net section of the Properties panel.
7. The Pour Over Same Net section in the Properties panel determines how the polygon interacts with other objects in the same net.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/polygon-properties.png" alt="Polygon Pour Properties"  style="max-width: 100%; height: auto;"/>
    </div>

8. To ensure that the polygon remains intact after any modifications are made, enable Repour All at the top in Tools -> Polygon Pours.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/repour-all.png" alt="Repour All"  style="max-width: 100%; height: auto;"/>
    </div>

### Via

A via is a connection between different layers of a board. These come in 3 types:

- ^^Through-hole (1)^^
- Blind (2)
- Buried (3)

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/via-types.png" alt="Via Types"  style="max-width: 40%; height: auto;"/>
</div>

<br>

On the team, we exclusively use through-hole vias. To add a via:

1. Select Via from the toolbar.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/toolbar-via.png" alt="Via in Toolbar"  style="max-width: 60%; height: auto;"/>
    </div>

2. Move mouse to position and you can press the Alt key to restrict vertical or horizontal movement (this may be useful for alignment). Click to place in the desired position.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/place-via.png" alt="Placing Via"  style="max-width: 100%; height: auto;"/>
    </div>

3. Assign a net to the via in the Properties panel.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/via-net.png" alt="Assigning Net to Via"  style="max-width: 100%; height: auto;"/>
    </div>

## Board Shape

Defining the board shape is an important step in the PCB design process. The following shows an empty board, but this can be done after component placement and routing is complete.

One way to set the board shape is to define it based on an existing shape:

1. First, draw the shape of the board as you like using primitives (i.e. lines, arcs, shapes).

2. After ensuring the shape follows the border region you intend, go to Design -> Board Shape -> Define Board Shape from Selected Objects

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/board-shape-objects.png" alt="Defining Board Shape from Selected Objects"  style="max-width: 100%; height: auto;"/>
    </div>

3. Alternatively, you can define/edit the board shape by pressing the 1 key, and going to Design:

<div style="text-align: center; margin-top: 30px;">
    <img src="/../../Hardware/Altium/Images/board-shape-design.png" alt="Defining Board Shape with Design"  style="max-width: 100%; height: auto;"/>
</div>


## Design Rule Checker

To confirm that the design conforms to rules, you must do a Design Rule Check, which checks all elements of the PCB against the enabled design rules (this includes things like minimum clearance rules, etc...).

1. Go to Tools -> Design Rule Check.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/design-rule-check.png" alt="Accessing Design Rule Check"  style="max-width: 100%; height: auto;"/>
    </div>

2. You can edit settings as necessary, both for the report file and the rules being checked.
3. Run Design Rule Check.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/drc-options.png" alt="Design Rule Check Options and Run"  style="max-width: 100%; height: auto;"/>
    </div>

4. A window should appear with messages describing any violations.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/drc-errors.png" alt="Design Rule Check Errors"  style="max-width: 100%; height: auto;"/>
    </div>

## Silk Screen

The silk screen is a layer of the board which has labelling and graphics. These are not linked to the circuit itself, but provide important information to anyone looking at the board. On Altium, this is the Top and Bottom Overlay.

### Labels 

By default, all components on the PCB are labelled with the [component designators](../../Hardware/Altium/schematic-basics.md/#component-designators), the formatting of which can be modified. Generally, you will want to make a few specific changes:

#### True Type Text

1. Select one of the labels and right-click.
2. On the menu, select "Find Similar Objects" and "Ok". This should select all of the component labels.
3. In the Properties panel, select "TrueType" in the Font section.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/true-type.png" alt="TrueType"  style="max-width: 100%; height: auto;"/>
    </div>

4. Depending on the use, you may choose to make the text inverted (particularly for the text you want to make stand out).

### Images

Most boards will also require graphics, like the RIT Racing logo. Files for some commonly used ones can be found [here](../../Hardware/Resources/silk-screen-files.md) (Hardware -> Resources -> Silk Screen Files). 

1. Download the desired image if you don't have it already.
2. On the PCB document, ensure you are on the right layer.
3. Go to Place -> Graphics.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/place-graphic.png" alt="Placing Graphic"  style="max-width: 100%; height: auto;"/>
    </div>

4. Drag to select space you want the graphic to occupy.
5. A window will open showing your file system. Select the image you want to use.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/select-image.png" alt="Selecting Image for Graphic"  style="max-width: 100%; height: auto;"/>
    </div>

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/image-settings.png" alt="Confirming Graphic Options"  style="max-width: 100%; height: auto;"/>
    </div>

6. The graphic should appear as part of the silk screen.

## Further Reading

This is just a brief introduction to PCB design.

For more specifics and questions, look at the [Resources](../../Hardware/Resources/learning.md) page, where you can find links to explore all of Altium's features and capabilities as well as general knowledge about PCBs.