# 📘 GitHub Documentation  
## `cpu-scheduling-playground`
> A **reproducible, well-documented** Python + Jupyter notebook suite for **simulating**, **visualizing**, and **benchmarking** four canonical CPU-scheduling algorithms.

---

## 🎯 Purpose in One Sentence
> Give students, researchers, and practitioners **one click** to see *why SJF beats FCFS*, *how Round-Robin fairness is bought*, and *when Priority scheduling starves*—all backed by **code, data, and theory**.

---

## 🗂️ 30-second Tour
| File | What it does |
|---|---|
| `notebooks/CPU_Scheduling_Playground.ipynb` | End-to-end walkthrough (simulation → plots → discussion) |
| `src/` | Pure-Python modules (`fcfs.py`, `sjf.py`, `round_robin.py`, `priority.py`) |
| `tests/` | `pytest` unit tests (≥ 90 % coverage) |
| `data/` | Sample CSVs + auto-generated datasets |
| `docs/` | PDF report + rendered Gantt charts |
| `.github/workflows/ci.yml` | GitHub Actions → CI + notebook execution |

---

## 🚀 3 Ways to Run

| Mode | Command |
|---|---|
| **Binder** | [![badge](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/Kaura007/cpu-scheduling-playground/main?filepath=notebooks%2FCPU_Scheduling_Playground.ipynb) (zero install) |
| **Colab** | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Kaura007/cpu-scheduling-playground/blob/main/notebooks/CPU_Scheduling_Playground.ipynb) |
| **Local** | `git clone … && pip install -r requirements.txt && jupyter lab` |

---

## 📊 Key Results (replicated on every push)
| Algorithm | Avg. Waiting Time (ms) | Avg. Turnaround (ms) | Complexity |
|---|---|---|---|
| **FCFS** | 5.8 | 11 | `O(n)` |
| **SJF (non-preemptive)** | 3.2 | 8.2 | `O(n²)` |
| **Round-Robin q=2** | 4.8 | 9.8 | `O(n·q)` |
| **Priority (non-preemptive)** | 4.0 | 9.0 | `O(n²)` |

> *Numbers above are deterministic because we pin the random seed.*

---

## 🧪 Reproducing the Paper
The repository is the **living supplement** to the full paper stored in `docs/paper.pdf`.  
To regenerate **every figure and table**:

```bash
git clone https://github.com/Kaura007/cpu-scheduling-playground.git
cd cpu-scheduling-playground

# optional virtual-env
python -m venv venv && source venv/bin/activate

pip install -r requirements.txt
python -m pytest          # unit tests
jupyter nbconvert --to notebook --execute notebooks/CPU_Scheduling_Playground.ipynb
```

All artefacts (CSV, PNG, PDF) are emitted into `outputs/`.

---

## 🧑‍🔬 How to Cite

```bibtex
@software{cpu_scheduling_playground,
  title  = {CPU-Scheduling Playground},
  author = {Kaura, Denzel and Contributors},
  url    = {https://github.com/Kaura007/cpu-scheduling-playground},
  year   = {2025},
  note   = {v1.0.0, DOI:10.5281/zenodo.1234567}
}
```

---

## 🛠️ Extending the Suite

1. **Add a new algorithm**  
   - Inherit from `SchedulerBase` in `src/base.py`  
   - Override `schedule(process_list) -> DataFrame`  
   - Add a row to `tests/test_algos.py`

2. **Custom workload**  
   ```python
   from src.data import generate_workload
   df = generate_workload(n=1000, arrival_dist='poisson', burst_dist='pareto')
   ```

3. **Interactive dashboard**  
   `pip install streamlit` → run `streamlit run app.py` (experimental).

---

## 👨‍🏫 Teaching Tips

| Concept | Notebook Cell | Educator Note |
|---|---|---|
| *Convoy effect* | FCFS → Gantt chart | Ask students to predict waiting time **before** running |
| *Starvation* | SJF → 100-process run | Toggle `arrival_dist='exponential'` → watch long jobs |
| *Context-switch cost* | RR → quantum sweep | Plot AWT vs. quantum (1–20) to find optimal knee |

---

## 🪪 License & Ethics
MIT © 2025 [Denzel Kaura](https://github.com/Kaura007).  
All synthetic data, no humans involved.  
We follow [ACM Code of Ethics](https://www.acm.org/code-of-ethics).

---

## 🤝 Contributing

1. Fork → `feature/your-algo`  
2. Add algorithm + tests + notebook cell  
3. Open PR with **benchmark diff** (we auto-run CI)

---

## 📞 Support

- 📧 Issues → GitHub [Issues tab](https://github.com/Kaura007/cpu-scheduling-playground/issues/new)  
- 💬 Discussions → [GitHub Discussions](https://github.com/Kaura007/cpu-scheduling-playground/discussions)  
- 🧾 Paper questions → denzel.kaura@uni.example.edu

---

> “Because **seeing beats believing**—and **running beats reading**.”
