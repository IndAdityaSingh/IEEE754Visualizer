# 💻 IEEE 754 Floating-Point Visualizer (32-bit Single Precision)

A simple, graphical user interface (GUI) application built with **Tkinter** that converts a decimal number into its **IEEE 754 Single Precision (32-bit float)** binary and hexadecimal representation. It provides a color-coded breakdown and a step-by-step explanation of the conversion process.



---

## ✨ Features

* **Decimal to Binary/Hex Conversion:** Instantly converts any standard decimal number (e.g., `12.375`, `-0.5`) to its 32-bit IEEE 754 format.
* **Color-Coded Output:** Clearly separates the three main components of the 32-bit format:
    * 🔵 **Sign Bit (1 bit)**
    * 🟢 **Exponent (8 bits)**
    * 🔴 **Mantissa/Fraction (23 bits)**
* **Step-by-Step Breakdown:** Provides a detailed, human-readable explanation of the mathematical process, including:
    * Sign determination
    * Binary conversion of the number
    * Normalization to scientific notation
    * Biased Exponent calculation
    * Mantissa derivation
* **Hexadecimal Output:** Shows the final 8-character hexadecimal representation.
* **User-Friendly GUI:** Simple, responsive interface built with `tkinter` and `ttk` for a modern look and feel.

---

## 🚀 Installation & Setup

This application requires Python 3 and the standard `tkinter` library, which is usually included with most Python installations.

### Prerequisites

* Python 3.x

### Running the Application

1.  **Save the Code:** Save the provided code into a file named `ieee754_visualizer.py`.
2.  **Run from Terminal:** Open your terminal or command prompt, navigate to the directory where you saved the file, and run:

    ```bash
    python ieee754_visualizer.py
    ```

    The GUI window should open immediately.

---

## 📖 Usage

1.  **Enter a Number:** Type a decimal number (positive or negative) into the "Enter Decimal Number" field.
    * *Example: Enter* `12.375`
2.  **Convert:** Click the **Convert** button or press the **`Enter`** key.
3.  **View Results:**
    * The **Full 32-bit Binary Representation** will be displayed in the color-coded block.
    * The **Detailed Breakdown** table provides the value of each component and the hexadecimal equivalent.
    * The **Conversion Steps** section offers a comprehensive explanation of how the result was calculated.

---

## 🔧 Code Details

The core conversion logic uses Python's built-in `struct` module, which is the most reliable way to map a Python float (which is typically 64-bit double precision) to its raw 32-bit binary memory representation.

```python
# The key part of the conversion logic:
packed = struct.pack('!f', num)      # Packs the float 'f' into 4 bytes (little-endian: '<f', big-endian: '!f')
int_val = struct.unpack('!I', packed)[0] # Unpacks the 4 bytes as an unsigned 32-bit integer 'I'
full_bin = bin(int_val)[2:].zfill(32) # Converts the integer to its 32-bit binary string
