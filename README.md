# BULK
1) stride 
2) add dummy, the reason is because PIT/FLAT have 4 indexes Pt,O,H,, while bulk only 3, dummy is add as place holder
NOTE. you can still use the net with Pt, but you must set it as 0 on the mass in LAMMPS/CP2k

# GPU 
in case of run in multiple GPU, assuming 2, one can assign each gpu for specific run let say run1 for device 0 and run2 for device 1.
the most common run is 
```bash
export CUDA_VISIBLE_DEVICES=0
```
or 
```bash
export CUDA_VISIBLE_DEVICES=1
```
however, if run this at the same terminal its going to be overwrite hence only the last will be taken, therefore, here are some way on how to do it 
# CUDA Launch Cheat Sheet

## 🔹 1. Run on one specific GPU
```bash
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=0 dp train input.json
```
- Uses **physical GPU0** (as seen in `nvidia-smi`).  
- Inside the process, this appears as **GPU 0**.  

---

## 🔹 2. Run in background + save logs
```bash
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=1 dp train input.json > run1.log 2>&1 &
```
- `> run1.log` → stdout to file  
- `2>&1` → stderr to same file  
- `&` → run in background  
- Check logs with:
  ```bash
  tail -f run1.log
  ```

---

## 🔹 3. Run multiple jobs in same shell (safe)
```bash
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=0 dp train input0.json > run0.log 2>&1 &
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=0 dp train input1.json > run1.log 2>&1 &
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=1 dp train input2.json > run2.log 2>&1 &
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=1 dp train input3.json > run3.log 2>&1 &
```
- Two jobs on GPU0, two on GPU1.  
- Each has its own logfile.  

---

## 🔹 4. Run from separate shells/tabs
- Shell 1:
  ```bash
  export CUDA_VISIBLE_DEVICES=0
  dp train input.json
  ```
- Shell 2:
  ```bash
  export CUDA_VISIBLE_DEVICES=1
  dp train input.json
  ```

---

## 🔹 5. Launch all runs with one script
Create `launch_all.sh`:
```bash
#!/bin/bash
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=0 dp train input0.json > run0.log 2>&1 &
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=0 dp train input1.json > run1.log 2>&1 &
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=1 dp train input2.json > run2.log 2>&1 &
CUDA_DEVICE_ORDER=PCI_BUS_ID CUDA_VISIBLE_DEVICES=1 dp train input3.json > run3.log 2>&1 &
wait   # optional: wait for all to finish
```
Run with:
```bash
bash launch_all.sh
```

---

✅ Golden rule:  
- Inline `CUDA_VISIBLE_DEVICES=…` → **always safe** in a shared shell.  
- Export once and flip between runs → **risky**, easy to overlap jobs.  
