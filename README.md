# duodecaphonic-studio-schoenberg-mature-practice

An interactive browser-based twelve-tone composition studio and analytical score generator built around the ten interdependent features of Arnold Schoenberg's mature serial practice. Runs entirely client-side using the Web Audio API, HTML5 Canvas, and bitwise pitch-class set mathematics.

---

## Overview

Rather than treating twelve-tone serialism as a mechanical 12×12 lookup table, **duodecaphonic-studio-schoenberg-mature-practice** models the structural, contrapuntal, harmonic, and metric principles of Schoenberg's mature works (*Variations for Orchestra Op. 31*, *Klavierstück Op. 33a*, *Violin Concerto Op. 36*, *Fourth String Quartet Op. 37*, and *Moses und Aron*).

The engine synthesizes combinatorial row pairs, tracks 12-tone aggregates in real time, partitions sets across multiple voices, and aligns metric accents with invariant pitch-class intersections.

---

## Schoenberg's 10 Mature Features Implemented

1. **Hexachordal Inversional Combinatoriality:** Evaluates and constructs Prime rows ($P_0$) using 12-bit pitch-class masks so the first hexachord of $P_0$ and its paired inversion $I_n$ are mutually exclusive complements:
   $$\text{Hex}_A(P_0) \cap \text{Hex}_A(I_n) = \emptyset \quad \text{and} \quad \text{Hex}_A(P_0) \cup \text{Hex}_A(I_n) = \{0, 1, \dots, 11\}$$
2. **Aggregates:** Pairs combinatorial rows ($P_0 + I_n$) into 6+6 contrapuntal blocks so all 12 chromatic pitch classes are completed within every half-row span across active voices.
3. **Linear Set Presentation:** Routes complete, uninterrupted 12-note horizontal statements to the primary melodic voice (*Hauptstimme*, marked **H**) during thematic expositions.
4. **Partitioning:** Slices row forms into discrete dyads, trichords, and tetrachords distributed across contrasting registers and secondary voices (*Nebenstimme*, marked **N**).
5. **Isomorphic Partitioning:** Applies identical order-index sieves (such as `{0, 3, 6, 9}`, `{1, 4, 7, 10}`, `{2, 5, 8, 11}`) across consecutive row transformations to generate symmetrical intervallic motifs.
6. **Invariants:** Scans all 48 matrix forms to index preserved pitch-class dyads and trichords, highlighting shared notes on the matrix and using them as structural pivot points ($\star$) between row statements.
7. **Hexachordal Levels:** Organizes macro-form (*Exposition*, *Episode*, *Development*, *Recapitulation*) by grouping combinatorial row tetrads ($P_x, I_{x+n}, R_x, RI_{x+n}$) into formal transposition areas ($A_0 \dots A_{11}$).
8. **Set-Derived Harmony:** Constructs vertical accompaniment chords strictly from contiguous row segments and invariant subsets so vertical sonorities reflect the interval-class properties of the referential set.
9. **Pitch-Relational Metre:** Derives rhythmic weights, downbeats, and agogic accents dynamically from invariant pivot pitches, hexachord boundaries, and aggregate completion points.
10. **Multidimensional Set Presentations:** Unfolds single twelve-tone rows across both horizontal melodic lines and vertical accompaniment harmonies simultaneously.

---

## Studio Modules

### 1. Combinatorial Row Workbench
* **Authentic Schoenberg Presets:** Load the historical referential sets from *Op. 31*, *Op. 33a*, *Op. 36*, *Op. 37*, and *Moses und Aron*.
* **I-Combinatorial Synthesizer:** Generate new 12-tone rows guaranteed to possess Hexachordal Inversional Combinatoriality.
* **Custom Hexachord Builder:** Select any 6 chromatic pitch classes and automatically compute the complementary inversional hexachord to form a valid 12-tone row.

### 2. Interactive 12×12 Matrix & Invariant Explorer
* View all 48 canonical transformations ($P_0 \dots P_{11}$, $I_0 \dots I_{11}$, $R_0 \dots R_{11}$, $RI_0 \dots RI_{11}$) with hexachordal split dividers.
* Toggle between pitch-letter notation (`C, C#, D...`) and integer pitch-class notation (`0–11`).
* Highlight shared invariant dyads and trichords across all 48 row forms and click any row header to audition it instantly.

### 3. Hexachordal Levels & Partitioning Sequencer
* Assign transposed Hexachordal Areas ($A_0 \dots A_{11}$) to four formal sections: **Exposition**, **Episode**, **Development**, and **Recapitulation**.
* Select independent texture and partitioning strategies per section:
  * **Linear Hauptstimme** (6+6 combinatorial counterpoint)
  * **Partitioned Trichords & Dyads** (*Hauptstimme* / *Nebenstimme* / accompaniment split)
  * **Isomorphic Order Sieve** (`{0,3,6,9}` symmetrical order-position extraction)
  * **Multidimensional Set Harmony** (simultaneous horizontal and vertical unfolding)

### 4. Real-Time Analytical Score, Web Audio & MIDI Export
* **Scrolling Analytical Canvas:** Displays *Hauptstimme* (**H**), *Nebenstimme* (**N**), and Harmony (**Harm**) lanes with order indices, invariant pivot rings ($\star$), and dashed 12-tone aggregate completion markers.
* **Live Aggregate Completion Tracker:** 12 chromatic LEDs illuminate as each pitch class sounds and reset upon completion of the 12-tone aggregate.
* **Polyphonic Web Audio Synthesizer:** Built-in chamber voices (Chamber Strings, solo violin/viola/cello timbres, Viennese Piano, Clarinet/Horn/Bassoon Wind Trio).
* **Standard MIDI File (`.mid`) Export:** Exports a multi-track Format 1 MIDI file for use in any DAW or notation software (Dorico, Sibelius, MuseScore, Logic Pro, Ableton Live).

---

## Mathematical Reference

Given a Prime row $P_0 = [p_0, p_1, \dots, p_{11}]$ where $p_k \in \mathbb{Z}_{12}$:

* **Transposition ($P_t$):**
  $$P_t[k] = (P_0[k] + t) \bmod 12$$
* **Inversion ($I_t$):**
  $$I_0[k] = (12 - P_0[k]) \bmod 12, \quad I_t[k] = (I_0[k] + t) \bmod 12$$
* **Retrograde ($R_t$) & Retrograde Inversion ($RI_t$):**
  $$R_t[k] = P_t[11 - k], \quad RI_t[k] = I_t[11 - k]$$
* **Bitwise Hexachord Mask:**
  $$M(H) = \sum_{p \in H} 2^p, \quad M(\text{Hex}_A(P_0)) \oplus M(\text{Hex}_A(I_n)) = 4095 \text{ } (\text{binary } 111111111111_2)$$

---

## License

MIT License
