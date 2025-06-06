Once your project is completed, validated, and saved to the server, you can export it. This produces files in the formats expected by the PCB manufacturer (JLCPCB in this case). Specifically, there are two main types:

- ^^Gerber^^: serves as a blueprint for the PCB, providing information on the shape and position of copper traces, silkscreen, and solder mask.
- ^^NC Drill^^: provides information about the holes in the PCB, including location, size, depth, plating, and more.

---

## Gerber Files

1. Ensure you are in the PCB document in your project.

2. Navigate to **File → Fabrication Outputs → Gerber Files**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/export-gerber.png" alt="Access Gerber File Export"  style="max-width: 100%; height: auto;"/>
    </div>

3. In the window that opens, ensure the parameters are as follows:
    1. Units: Inches
    2. Decimal: 0.01 (this defines the coordinate precision)

4. In **Plot Layers** (at the bottom) choose **Select All** to ensure that every layer is included in the export.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/gerber-settings.png" alt="Gerber Export Settings"  style="max-width: 100%; height: auto;"/>
    </div>

5. Switch to the **Advanced Settings** tab at the top and ensure the parameters are set as follows:
    - Leading/Trailing Zeroes: Suppress leading zeroes (reduces file size).
    - Plotter Type: Unsorted (faster).
    - Others: Use software arcs.

6. Once all settings are verified, select **Apply**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/gerber-advanced-settings.png" alt="Gerber Export Advanced Settings"  style="max-width: 100%; height: auto;"/>
    </div>

7. The generated CAMTastic file will open. Rename this file to "Gerber".

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/rename-camtastic-file.png" alt="Rename CAMtastic file"  style="max-width: 100%; height: auto;"/>
    </div>

8. Navigate to the generated output files on your system. This path should be **Users → Public → Public Documents → Altium → Your project → Project Outputs**. Inside this folder, create a new folder named "Gerber". Move all the files into this folder.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/outputs-gerber-folder.png" alt="Project Outputs Gerber Folder"  style="max-width: 100%; height: auto;"/>
    </div>

That's the Gerber export complete.

## NC Drill Files

1. Return to the PCB document in Altium and navigate to **File → Fabrication Outputs → NC Drill Files**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/export-drill-files.png" alt="Access Drill Files Export"  style="max-width: 100%; height: auto;"/>
    </div>

2. In the setup window that pops up, ensure the following parameters are selected:

    - Units: Inches
    - Format: 2:4
    - Leading/Trailing Zeroes: Suppress trailing zeroes
    - Coordinate Positions: Reference to relative origin
    - Other: Optimize change location commands

3. Select **OK**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/drill-files-setup.png" alt="Setup Drill Files"  style="max-width: 50%; height: auto;"/>
    </div>

4. The **Import Drill Data** window will pop up. Select **OK** here as well.

5. As before, a generated CAMtastic file will open. Rename this file to "Drill".

6. Navigate to the same Project Outputs folder in your file system (**Users → Public → Public Documents → Altium → Your project → Project Outputs**).

7. Create a new folder named "Drill" and place all the new files there.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/outputs-drill-folder.png" alt="Project Outputs Drill Folder"  style="max-width: 100%; height: auto;"/>
    </div>

## File Compression

1. Create a third folder in the same Project Outputs directory (**Users → Public → Public Documents → Altium → Your project → Project Outputs**) named the same as the title of your project on Altium.

2. Move the Gerber and Drill folders into this new folder. Compress this folder. (On Windows: right-click and select **Compress to → ZIP file**.)

This ZIP file is your final output which can be sent by the Electronics Lead to JLCPCB for manufacturing.