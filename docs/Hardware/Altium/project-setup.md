---
hide:
  - toc
---

---

## New Project

1. In the toolbar at the top, navigate to **File → New → Project**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/create-new.png" alt="Create New"  style="max-width: 100%; height: auto;"/>
    </div>

2. A window will open where you can set the project's name, its local path, and its location on the RIT Racing server. After confirming, click **Save**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/set-new.png" alt="Set New"  style="max-width: 100%; height: auto;"/>
    </div>

## Add Schematic

1. Once the project loads, add a schematic: right-click on the project name and select **Add New to Project → Schematic**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/add-schematic.png" alt="Add Schematic"  style="max-width: 100%; height: auto;"/>
    </div>

2. A blank schematic will appear. 

3. You'll notice an asterisk (\*) and a red symbol next to the project name. This indicates that changes have been made but not yet saved to the server. To push the changes, click **Save to Server**.

4. The first time you save, you'll be asked to choose a local location. You can usually accept the default path, which will typically look llike this:

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/save-to-server.png" alt="Save to Server"  style="max-width: 100%; height: auto;"/>
    </div>

5. After saving locally, a window will display the modified files. You can choose which updates to push to the server (all are selected by default). Uncheck any files you don’t want to include, then click **OK**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/choose-modifications.png" alt="Choose Modifications"  style="max-width: 100%; height: auto;"/>
    </div>

6. The title block on the schematic displays key information like board name, author, revision number, and date. This information can be edited in **Properties → Title Block**


## Add PCB Document

1. To add a PCB design to the project, right-click on the project and go to **Add New to Project → PCB**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/add-pcb.png" alt="Add PCB"  style="max-width: 100%; height: auto;"/>
    </div>

2. A blank PCB document will appear. The bar at the bottom shows the different available layers. Once your schematic is complete, you can update this design with components.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/blank-pcb.png" alt="Blank PCB"  style="max-width: 100%; height: auto;"/>
    </div>

## Design Rules

To maintain consistency and ensure that designs conform to technical requirements, a standardized set of PCB design rules has to be imported to Altium for use in the team's projects. This is a .RUL file that will be provided to you. 

To import:

1. Go to **Design → Rules** in the top menu.
2. In the **PCB Rules and Constraints Editor**, right-click on the **Design Rules** folder on the top left and select **Import Rules**.
3. The **Choose Design Rule Type** panel will open. Select all (++ctrl+a++) and click **OK**.
3. Browse to the .RUL file and select it.
4. Click **Open**.