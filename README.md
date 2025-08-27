# Disk Generator — VS Code Edition

A VS Code–ready Streamlit app for generating **SolidWorks Equation-Driven Curve** parametric expressions for cycloidal disks, plus a live 0→2π preview.

## Open & Run in VS Code

1. **Open Folder** (`disk-generator/`) in VS Code.
2. Install the **Python** extension if prompted.
3. Create/activate a virtual env (one-time):
   - Windows (PowerShell):  
     `python -m venv .venv && .venv\\Scripts\\Activate.ps1`
   - macOS/Linux (bash/zsh):  
     `python -m venv .venv && source .venv/bin/activate`
4. Install deps:  
   - Task: `Terminal → Run Task → Install Python dependencies`, **or**  
   - Terminal: `pip install -r requirements.txt`
5. Press **F5** (or the green Run arrow): *Run Disk Generator (Streamlit)*.  
   VS Code opens a local URL (usually `http://localhost:8501`) — click it.

> Windows note: if activation is blocked, run PowerShell as Admin once:
> `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`

## Using the Output in SolidWorks
1. Sketch → **Tools → Sketch Entities → Equation Driven Curve**.
2. Choose **Parametric** mode.
3. Paste **x(t) expression** and **y(t) expression** from the app (expressions only, no `x=` or `y=`).
4. Set **t1 = 0**, **t2 = 2*pi** (radians). If a fully closed loop errors, try `2*pi - 1e-6`.

**SolidWorks rules baked in**
- Trig uses **radians**.
- Use **`atn`** for arctangent in SW equations.
- Global Variables can’t be referenced directly in the curve editor (tie a **dimension** to a GV if needed).

## Libraries (PyPI links)
- Streamlit — UI: https://pypi.org/project/streamlit/  
- NumPy — numerics: https://pypi.org/project/numpy/  
- Matplotlib — plotting: https://pypi.org/project/matplotlib/

## Inputs (hover tooltips in the app)
- **R_p** — pitch circle radius of fixed pins (mm).  
- **e** — eccentricity of the cycloid (mm).  
- **r** — radius of each fixed pin (mm).  
- **N** — number of fixed pins.

## Troubleshooting
- If the app warns that `R_p/(e*N) ∈ [-1,1]`, the `atn` denominator may hit zero → SW might fail. Adjust parameters.
- If the preview is a single dot/line, check magnitudes (units mm). Try larger `R_p` or smaller `e`/`r`.
