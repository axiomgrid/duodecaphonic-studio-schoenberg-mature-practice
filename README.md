# duodecaphonic-studio-schoenberg-mature-practice

**Vibecoded by Lorenzo Granado**

An interactive browser-based twelve-tone composition studio and analytical score generator built around the ten interdependent features of Arnold Schoenberg's mature serial practice. Runs entirely client-side using the Web Audio API, HTML5 Canvas, and bitwise pitch-class set mathematics.

---

## Overview

Rather than treating twelve-tone serialism as a mechanical 12×12 lookup table, **duodecaphonic-studio-schoenberg-mature-practice** models the structural, contrapuntal, harmonic, and metric principles of Schoenberg's mature works (*Variations for Orchestra Op. 31*, *Klavierstück Op. 33a*, *Violin Concerto Op. 36*, *Fourth String Quartet Op. 37*, and *Moses und Aron*).

The engine synthesizes combinatorial row pairs, tracks 12-tone aggregates in real time, partitions sets across multiple voices, and aligns metric accents with invariant pitch-class intersections.

---

## Schoenberg's 10 Mature Features Implemented

1. **Hexachordal Inversional Combinatoriality:** Evaluates and constructs Prime rows ($P_0$) using 12-bit pitch-class masks so the first hexachord of $P_0$ and its paired inversion $I_n$ are mutually exclusive complements:
2. 
