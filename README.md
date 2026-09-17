# 4×4 Keypad and LED Interfacing Using Raspberry Pi Pico

## 1. Title / Experiment Name

**4×4 Keypad and LED Interfacing Using Raspberry Pi Pico**

---

## 2. Aim

To interface a 4×4 matrix keypad and 12 LEDs with a Raspberry Pi Pico using GPIO pins and control the LEDs according to the key pressed on the keypad using Python/MicroPython.

---

## 3. Objectives

* Understand the working of a 4×4 matrix keypad.
* Interface a keypad with GPIO pins.
* Interface multiple LEDs with GPIO pins.
* Scan keypad rows and columns using Python.
* Control individual and groups of LEDs based on keypad input.
* Implement and test the circuit using Wokwi simulation.

---

## 4. Requirements / Components Required

| S.No | Component                  | Quantity    |
| ---- | -------------------------- | ----------- |
| 1    | Raspberry Pi Pico          | 1           |
| 2    | 4×4 Matrix Keypad          | 1           |
| 3    | LEDs                       | 12          |
| 4    | Current limiting resistors | 12          |
| 5    | Connecting wires           | As required |
| 6    | Wokwi Online Simulator     | 1           |
| 7    | MicroPython                | 1           |

> For a physical circuit, a resistor is normally used with each LED to limit current.

---

## 5. Theory

A 4×4 matrix keypad consists of 16 keys arranged in 4 rows and 4 columns. Instead of connecting every key separately, the keypad uses 8 GPIO connections: 4 row lines and 4 column lines.

### Keypad Arrangement

|    | C1 | C2 | C3 | C4 |
| -- | -- | -- | -- | -- |
| R1 | 1  | 2  | 3  | A  |
| R2 | 4  | 5  | 6  | B  |
| R3 | 7  | 8  | 9  | C  |
| R4 | *  | 0  | #  | D  |

The Raspberry Pi scans the keypad by activating one row at a time and reading the column inputs. When a key is pressed, it electrically connects one particular row and column. The program identifies the pressed key from this row-column combination.

The LEDs are connected to GPIO output pins. When a GPIO output is HIGH, the corresponding LED turns ON. When it is LOW, the LED turns OFF.

---

## 6. Circuit / Pin Connections

### LED Connections

| LED   | GPIO    |
| ----- | ------- |
| LED1  | GPIO 11 |
| LED2  | GPIO 10 |
| LED3  | GPIO 9  |
| LED4  | GPIO 8  |
| LED5  | GPIO 7  |
| LED6  | GPIO 6  |
| LED7  | GPIO 5  |
| LED8  | GPIO 4  |
| LED9  | GPIO 3  |
| LED10 | GPIO 2  |
| LED11 | GPIO 28 |
| LED12 | GPIO 27 |

### Keypad Connections

| Keypad Pin | GPIO    |
| ---------- | ------- |
| R1         | GPIO 26 |
| R2         | GPIO 22 |
| R3         | GPIO 21 |
| R4         | GPIO 20 |
| C1         | GPIO 19 |
| C2         | GPIO 18 |
| C3         | GPIO 17 |
| C4         | GPIO 16 |

---

## 7. Keypad Configuration

### Keypad Layout

|    | C1 | C2 | C3 | C4 |
| -- | -- | -- | -- | -- |
| R1 | 1  | 2  | 3  | A  |
| R2 | 4  | 5  | 6  | B  |
| R3 | 7  | 8  | 9  | C  |
| R4 | *  | 0  | #  | D  |

### Rows

```text
R1 = GPIO 26
R2 = GPIO 22
R3 = GPIO 21
R4 = GPIO 20
```

### Columns

```text
C1 = GPIO 19
C2 = GPIO 18
C3 = GPIO 17
C4 = GPIO 16
```

---

## 8. Working Principle

1. The program continuously scans the four keypad rows.
2. One row is made LOW while the other rows remain HIGH.
3. The four column inputs are then read.
4. If a key is pressed, one column becomes LOW.
5. The row-column combination identifies the key.
6. The program performs the corresponding LED operation.

---

## 9. Procedure

1. Open the provided Wokwi project:
   https://wokwi.com/projects/300124198602277389

2. Make sure the simulated board is a Raspberry Pi Pico.

3. Connect the 12 LEDs according to the GPIO table.

4. Connect the 4×4 keypad according to the row and column GPIO table.

5. Create or open the `main.py` file in the Wokwi MicroPython project.

6. Enter the Python program given in this repository.

7. Start the Wokwi simulation.

8. Press the keypad buttons one at a time.

9. Observe the corresponding LEDs.

10. Verify all 16 keypad operations using the operation table.

---

## 10. Program

The complete MicroPython program is available in:

```text
main.py
```

The program:

* Initializes 12 LEDs as GPIO outputs.
* Initializes four keypad rows as outputs.
* Initializes four keypad columns as inputs with pull-up resistors.
* Scans the keypad continuously.
* Detects the pressed key.
* Performs the corresponding LED operation.

---

## 11. Key Functions / Operation Table

| Key | Operation     |
| --- | ------------- |
| 1   | LED1 ON       |
| 2   | LED2 ON       |
| 3   | LED3 ON       |
| 4   | LED4 ON       |
| 5   | LED5 ON       |
| 6   | LED6 ON       |
| 7   | LED7 ON       |
| 8   | LED8 ON       |
| 9   | LEDs 1–8 ON   |
| 0   | LEDs 1–8 OFF  |
| A   | LED9 ON       |
| B   | LED10 ON      |
| C   | LED11 ON      |
| D   | LED12 ON      |
| *   | LEDs 9–12 ON  |
| #   | LEDs 9–12 OFF |

---

## 12. Expected Output

The expected output is that the LEDs respond according to the key pressed on the 4×4 keypad.
<img width="1919" height="1025" alt="Screenshot 2026-09-17 184429" src="https://github.com/user-attachments/assets/da8caca2-bfc6-4d09-a86c-d4a0e3e675db" />

For example:

```text
Press 1 → LED1 ON
Press 2 → LED2 ON
Press 3 → LED3 ON

Press 9 → LEDs 1–8 ON
Press 0 → LEDs 1–8 OFF

Press A → LED9 ON
Press B → LED10 ON
Press C → LED11 ON
Press D → LED12 ON

Press * → LEDs 9–12 ON
Press # → LEDs 9–12 OFF
```

---

## 13. Result

The 4×4 keypad and 12 LEDs were successfully interfaced with the Raspberry Pi Pico using GPIO pins and MicroPython. The keypad was scanned using row and column detection, and the LEDs were controlled according to the assigned keypad operations.

The experiment was successfully implemented and verified using Wokwi simulation.

**Result: Experiment completed successfully.**
