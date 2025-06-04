In Altium, libraries store all components used in schematic and PCB designs—including symbols, footprints, and part numbers.

The New Library contains a collection of commonly used components for team projects. Components can be selected from this library or added if they aren’t already available. This ensures consistent symbols, footprints, and part data across all designs.

---

## Use Existing Components

To add components from the library:

1. Click the **Panels** button on the bottom right corner and go to **Explorer**. In the window that pops up, navigate to **Components → New_Library** and click on **Components**. A list should appear in the section on the right.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/components-library.png" alt="Components Library"  style="max-width: 100%; height: auto;"/>
    </div>

2. The folder is further split into different component types (eg., resistors, capacitors, ICs, etc.) Each component has a name and description listed. When selected, details of the component appear in the panel below. This includes footprints of the parts associated with the component.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/selecting-component.png" alt="Selecting Component"  style="max-width: 100%; height: auto;"/>
    </div>

3. Right-click **→ Place** or drag the component onto the schematic.

---

## Add a New Component

1. Search for the part you need on [Digikey](https://www.digikey.com/).

2. Click the link in EDA/CAD Models.

    <div style="text-align: center; margin-top: 30px;">
      <img src="/../../Hardware/Altium/Images/digikey-search.png" alt="Searching Digikey"  style="max-width: 85%; height: auto;"/>
    </div>

3. Choose one of the downloads (e.g., Ultra Librarian).

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/select-download.png" alt="Select Download"  style="max-width: 85%; height: auto;"/>
    </div>

4. Choose Altium as the download format (no need to select 3D CAD model).

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/download-format.png" alt="Download Format"  style="max-width: 50%; height: auto;"/>
    </div>

5. The ZIP file will download to your computer. Extract it in your preferred folder.
6. On Altium go to **File → Run Script**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/run-script.png" alt="Run Script"  style="max-width: 25%; height: auto;"/>
    </div>

7. A window will pop up. Here, select **Browse → From file**.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/select-item-to-run.png" alt="Select Item to Run"  style="max-width: 55%; height: auto;"/>
    </div>

8. Select the file (it should begin with "UL_Import").

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/select-ul-import.png" alt="Select UL Import"  style="max-width: 70%; height: auto;"/>
    </div>

9. Select the one that says UL_Form.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/select-ul-form.png" alt="Select UL Form"  style="max-width: 50%; height: auto;"/>
    </div>

10. In the UL Import window that pops up, select **File** and choose the text document.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/select-text-file.png" alt="Select Text File"  style="max-width: 70%; height: auto;"/>
    </div>

11. The component documents should appear in the left panel of Altium under your open projects. For files ending in ".PcbDoc": if the content appears blank, try closing and reopening the document.

12. In the Explorer panel, navigate to **New_Library → Components → [appropriate component type]**.
13. Click **Add Component** in the top right.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/add-component-new-library.png" alt="Add Component in New Library"  style="max-width: 70%; height: auto;"/>
    </div>

14. Add the component name and manufacturer part number (under **Parameters**) to the sections on the left.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/new-component-details.png" alt="New Component Details"  style="max-width: 70%; height: auto;"/>
    </div>

15. For both the symbol and footprint:
    1. Select **Wizard → New**.
    2. Copy and paste the symbol/footprint from the respective files.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/new-component-documents.png" alt="New Component Documents"  style="max-width: 70%; height: auto;"/>
    </div>

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/add-docs-to-new-component.png" alt="Add Symbol and Footprint to New Component"  style="max-width: 70%; height: auto;"/>
    </div>

16. Right-click on the new component tab and **Save**.
17. **Save to Server**.
18. When creating or editing a component, be sure to add a comment such as "Created/Edited on *[current date]*" in the Release Notes window that appears.

    <div style="text-align: center; margin-top: 30px;">
        <img src="/../../Hardware/Altium/Images/component-release-notes.png" alt="Component Release Notes"  style="max-width: 60%; height: auto;"/>
    </div>
