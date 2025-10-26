# 🧠 What Is Circuitikz?

**Circuitikz** is a LaTeX package that lets you **draw electrical and electronic circuit diagrams** using code.
It’s built on top of **TikZ**, which is a powerful graphics library for LaTeX.

So when you write something like:

```latex
\begin{circuitikz}
  \draw (0,0) to[V=5<\volt>] (0,2)
        to[R=10<\ohm>] (2,2)
        -- (2,0) -- cycle;
\end{circuitikz}
```

you get a beautiful circuit diagram rendered automatically when you compile the `.tex` file.

---

# 🧰 Installation Options (Windows 11)

You have **two main ways** to get Circuitikz running:

---

## 🅰️ Option 1 — Native Windows Setup (Simplest for Beginners)

### Step 1: Install a LaTeX Distribution

Choose one of these:

* **[MiKTeX](https://miktex.org/download)** (recommended for Windows)
* **TeX Live** (more Linux-like, slightly heavier)

🧭 **Steps:**

1. Download and run the **MiKTeX Installer**.
2. During setup, **enable “Install missing packages on the fly”** — this lets MiKTeX auto-install Circuitikz the first time you use it.

### Step 2: Install a LaTeX Editor

Pick an editor you like:

* **TeXworks** (comes with MiKTeX)
* **TeXstudio**
* **VS Code + LaTeX Workshop plugin** (highly recommended if you like code editors)

### Step 3: Create a Test File

Save this as `test_circuit.tex`:

```latex
\documentclass{standalone}
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz}[american voltages]
  \draw
  (0,0) node[ground]{}
    to[V=5<\volt>] (0,2)
    to[R=10<\kilo\ohm>, v^>=?] (2,2)
    -- (2,0) -- cycle;
\end{circuitikz}
\end{document}
```

### Step 4: Compile It

In your editor:

* Click **“Compile” → “PDFLaTeX”** (or press `Ctrl+T` in TeXstudio).

✅ You should see a **schematic** of a resistor and voltage source in the PDF output.

---

## 🅱️ Option 2 — Using WSL2 (For Developers or Linux Users)

If you prefer working in a terminal, you can install Circuitikz in **WSL2 (Ubuntu)** and compile `.tex` files there.

### Step 1: Open Ubuntu in WSL2

Launch your WSL terminal.

### Step 2: Install TeX Live and Circuitikz

Run:

```bash
sudo apt update
sudo apt install texlive texlive-latex-extra texlive-pictures texlive-science
```

👉 The `texlive-pictures` and `texlive-science` packages include **Circuitikz**.

### Step 3: Verify Installation

Check if Circuitikz is available:

```bash
kpsewhich circuitikz.sty
```

If it returns a file path (e.g., `/usr/share/texlive/...`), it’s installed.

### Step 4: Compile a Test File

Create `test_circuit.tex` (same content as above).

Then compile with:

```bash
pdflatex test_circuit.tex
```

This will create `test_circuit.pdf` in your working directory.

To open it from Windows:

```bash
explorer.exe test_circuit.pdf
```

✅ You’ll see your Circuitikz diagram rendered beautifully!

---

# 💡 Bonus: Use VS Code (Cross-Platform, Modern Setup)

If you like coding environments, this is a great hybrid setup:

1. Install **VS Code**
2. Add the **LaTeX Workshop** extension
3. Use either **MiKTeX (Windows)** or **TeX Live (WSL)** as the backend
4. Create and compile `.tex` files directly from VS Code

---

# 🧩 Optional — Portable / Advanced Tools

| Tool                               | Purpose                                                                    |
| ---------------------------------- | -------------------------------------------------------------------------- |
| **Overleaf**                       | Online LaTeX editor — no installation, supports Circuitikz out of the box. |
| **TikZEdt**                        | GUI helper for TikZ diagrams.                                              |
| **Inkscape + Circuitikz exporter** | Convert drawn circuits to LaTeX code.                                      |

---

# ⚡ Troubleshooting

| Problem                                           | Solution                                                    |
| ------------------------------------------------- | ----------------------------------------------------------- |
| `! LaTeX Error: File 'circuitikz.sty' not found.` | Install `texlive-pictures` or enable auto-install in MiKTeX |
| Output looks pixelated                            | Compile with `pdflatex`, not older compilers                |
| Can’t find output PDF                             | Check the working directory or set `--output-directory=out` |

---

# 🧠 Summary

✅ **Circuitikz Setup Options**

| Setup                       | Tools                         | Best For                |
| --------------------------- | ----------------------------- | ----------------------- |
| **Native Windows (MiKTeX)** | MiKTeX + TeXstudio or VS Code | Quick and easy          |
| **WSL2 (TeX Live)**         | Ubuntu CLI + VS Code          | Developers, Linux users |
| **Overleaf (Web)**          | Browser only                  | Zero setup              |

Once installed, you can start drawing circuits directly inside your LaTeX documents or generate PDFs to include in your embedded systems notes, design reports, or documentation.

---

Guide created by Electric and Electronic Circuit Tutor GTP 5, and edited by me [Archibald](https://github.com/archibald-carrion)