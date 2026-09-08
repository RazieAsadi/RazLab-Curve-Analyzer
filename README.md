# RazLab Curve Analyzer

## About the Project

**RazLab Curve Analyzer** is an independent software project developed with the goal of providing a simple and practical tool for extracting numerical data from curves and graphs presented as images.

The project is designed with scientific and engineering applications in mind and aims to simplify the process of converting information contained in graph images into usable numerical data. The software allows users to import a graph image, calibrate its axes, and extract the required data without relying on complex tools or workflows.

Version **1.0.0** is the first release of the project and focuses on providing a practical set of core features for graph data extraction. Additional features and tools may be added in future versions.

---

## Overview

**RazLab Curve Analyzer** is a software application designed to extract numerical data from curves and graphs provided as images.

Researchers and engineers in fields such as **materials science, metallurgy, chemistry, nanotechnology, mechanical engineering, electrical engineering, and other scientific and engineering disciplines** use various instruments and experimental methods to analyze materials and systems. Many of the results obtained from these methods are presented as curves or graphs, including examples such as **FTIR, UV-Vis spectroscopy, XRD, thermal analysis methods such as DSC and TGA, stress-strain curves, and certain electrochemical measurements**.

In many cases, complete numerical data from a graph is not available, and only an image of the graph can be accessed. In research papers, authors may also present only selected data points from a curve, while other researchers may need additional data from the same graph.

RazLab Curve Analyzer was developed to simplify this process. The software allows users to import an image of a graph, calibrate its X and Y axes, define the curve path either automatically or manually, and extract X and Y data from the curve.

This functionality can be useful for **reconstructing approximate numerical data from graphs published in research papers, analyzing experimental results, and preparing data for further processing**. For example, extracted data may be used in data analysis or machine-learning projects. However, the accuracy of the extracted data depends on image quality and how accurately the curve path is defined.

Other software tools for graph digitization are available, but some are commercial or provide more complex interfaces and workflows. RazLab Curve Analyzer is designed as a free and straightforward tool for making data extraction from graph images more accessible.

The software provides two main approaches for defining a curve:

* **Auto Curve:** A fast method for extracting a curve path from suitable images.
* **Manual Curve:** A manual method that allows the user to define the curve path directly and is useful for more difficult graphs, lower-quality images, or curves that cannot be reliably detected automatically.

---

## Features

* Graph image loading
* Support for PNG, JPG, JPEG, BMP, TIF, and TIFF image formats
* X and Y axis calibration
* Conversion of image pixel coordinates to graph coordinates
* Automatic curve path extraction
* Manual curve path definition
* Extraction of a user-defined number of X and Y points from a curve
* Selection and extraction of arbitrary points from the graph
* Selection of points that do not necessarily lie on the curve
* Automatic Peak and Valley detection
* Display of extracted data
* Excel data export
* Zoom
* Pan
* Fit Image
* Delete Points
* Clear Path
* Resetting previous graph information when a new image is loaded

---

## How It Works

The general workflow of the application is:

**Load Image**

↓

**Set Origin, X Reference and Y Reference**

↓

**Calibration**

↓

**Curve Selection**

*(Auto Curve / Manual Curve)*

↓

**Data Extraction**

↓

**Extracted Data**

↓

**Download Data**

*(Excel)*

During **Data Extraction**, users can specify the desired number of points to extract or use **Selected Points** to directly select individual points from the image.

Extracted curve data, Peak/Valley information, and Selected Points are displayed in the extraction window and can be exported to an Excel file.

---

## Usage

### 1. Load an Image

Run the application and click **Load Image**.

Supported image formats are:

* PNG
* JPG
* JPEG
* BMP
* TIF
* TIFF

After loading, the graph image will be displayed in the application.

---

### 2. Set the Origin

Click **Origin** and select the desired point on the image.

You can use the mouse wheel or the middle mouse button to zoom the image and improve the accuracy of point selection.

The selected Origin point is used for calibration and does not necessarily have to be located exactly at the actual intersection of the X and Y axes.

After selecting the point, enter its corresponding X and Y values in the input fields.

If necessary, the Origin point can be repositioned using the left mouse button.

#### Origin Considerations

In **Auto Curve** mode, the position of the Origin affects the region in which the algorithm can search for the curve path.

If the Origin is moved upward along the Y-axis, the algorithm can still form a path at Y values below the Origin.

However, if the Origin is moved to the right along the X-axis and part of the curve exists at X values smaller than the Origin position, Auto Curve will not be able to detect that portion of the curve.

This limitation does not apply to **Manual Curve**.

---

### 3. Set X Reference and Y Reference

After defining the Origin, set the **X Reference** and **Y Reference** points.

For **X Reference**, select a point on the X-axis where the corresponding X value is clearly known from the image.

The important part is accurately positioning the point along the X-axis. Its position in the Y direction does not need to be exact because the point is automatically aligned with the Origin during calibration.

For **Y Reference**, select a point on the Y-axis and enter its corresponding Y value. In this case, the important part is accurately positioning the point along the Y-axis.

---

### 4. Calibration

Once the Origin, X Reference, and Y Reference have been defined, the **Calibrate** button becomes available.

Clicking **Calibrate** performs the axis calibration. The Reference points are automatically aligned with the Origin when necessary.

After calibration, moving the mouse over the graph displays the corresponding X and Y coordinates below the image.

Curve selection and data extraction tools can also be used after calibration.

---

### 5. Fit Image

Use **Fit Image** whenever you want to return the image to its appropriate initial viewing size.

---

## Auto Curve

To use automatic curve extraction, click **Auto Curve** and then select a point on the desired curve.

You can zoom the image to make the starting-point selection more precise.

Auto Curve generally works better with curves that have the following characteristics:

* Good image quality
* Clear color or visual contrast between the curve and its background
* A single curve or curves that do not overlap
* Peaks, valleys, or sharp features that are not excessively complex
* A continuous curve rather than a dotted or dashed path
* No text, symbols, or other graphical elements crossing the curve

Auto Curve may still work when some of these conditions are not satisfied, but the probability of incorrect path detection increases.

The main advantage of Auto Curve is its **speed when defining and extracting a curve path**.

---

## Manual Curve

If the image quality is poor, multiple curves overlap, or Auto Curve cannot reliably detect the desired path, **Manual Curve** can be used.

First, click **Manual Curve**. If an Auto Curve path has already been created, it will be removed.

Then click **Pen**.

In version 1.0.0, the Manual Curve section uses the Pen tool to define the curve path. The Pen button is provided separately from the Manual Curve button so that additional manual curve tools can potentially be added in future versions.

After activating Pen, the desired curve can be drawn manually.

Zooming the image can improve accuracy.

Click the starting point of the curve and then define subsequent points along the path.

Clicking and dragging allows the path to be shaped as a curve or **Bezier** segment. The interaction is conceptually similar to using a Pen tool in graphics software.

If a point is selected incorrectly, right-clicking removes the most recently drawn point, allowing the path to be continued from that location.

After completing the curve, click **Pen** again to deactivate it. This prevents accidental editing or deletion of points through right-clicking.

The complete path can also be removed using **Clear Path**.

---

## Selected Points

**Selected Points** allows users to extract the coordinates of specific points without defining an entire curve path.

After activating Selected Points, click anywhere on the image to select a point. The selected point will be displayed on the image.

The selected points do not necessarily have to lie on the curve.

Right-clicking removes the most recently selected point.

After finishing the selection process, deactivate Selected Points to prevent accidental deletion of points through right-clicking.

All selected points can be removed using **Delete Points**.

After selecting the desired points, click **Extract Data**. The selected point information will be displayed in the **Selected Points** tab.

---

## Data Extraction

After defining the curve path using Auto Curve or Manual Curve, enter the desired number of points in **Number of Points** and click **Extract Data**.

The **Extracted Data** tab displays the X and Y coordinates of the selected points along the curve.

The point-selection process attempts to preserve important features of the curve, including:

* The starting point
* The ending point
* Peaks
* Valleys

Additional points are then selected from the remaining sections of the curve.

If an important point overlaps with another selected point and would result in duplicate data, the duplicate selection is skipped and another point is selected from the path.

---

## Peak / Valley Detection

The **Peak / Valley** tab displays information about the Peaks and Valleys detected on the extracted curve path.

The accuracy of this detection depends on the extracted curve path.

With **Manual Curve**, Peaks and Valleys are calculated from the manually defined path, meaning that the analyzed path is the same path created by the user.

With **Auto Curve**, errors in curve-path detection may affect Peak and Valley detection as well.

If accurate coordinates of specific features such as Peaks or Valleys are required, users can use **Selected Points** to directly select those locations.

---

## Excel Export

After extracting the data, click **Download Data** to save the information displayed in the Extract Data window as an Excel file.

The Excel file contains the extracted data as well as Peak/Valley and Selected Points information.

---

## Starting a New Analysis

To analyze a new graph, click **Load Image** and select a new image.

Loading a new image resets the information associated with the previous graph and allows a new analysis to be started from the beginning.

---

## Installation

The Windows version of the application is provided as an installer.

To install the application:

1. Run **RazLab Curve Analyzer Setup.exe**.
2. Follow the installation steps.
3. Launch the application from the created shortcut or the Start Menu.

The Windows executable is packaged as a standalone application, so Python and the libraries used by the application do not need to be installed separately on the target computer.

---

## Technologies Used

* Python
* Tkinter
* NumPy
* Pillow
* OpenPyXL
* colorsys
* math
* PyInstaller
* Inno Setup

---

## Version

**Version 1.0.0**

---

## Project Status

This is the first public release of **RazLab Curve Analyzer**.

Additional features may be added in future versions, particularly in the area of manual curve definition.
