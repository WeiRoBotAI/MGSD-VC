# Multi-granularity semantic decoupling with vector constraints for micro-action recognition





The code is currently being organized.

## 😮 Highlights

- We rethink the MAR task from the perspective of the compositional semantic structure of category labels, and then propose a multi-granularity semantic decoupling and vector constraint method for MAR. This method reformulates holistic label supervision into structured, attributable, and fine-grained semantic guidance.
- We propose MGSD-VC, which consists of AWM, SSA, and SSD. AWM decomposes the label into three semantic branches: verbs, nouns, and phrases; SSA bridges the visual-semantic distribution differences; SSD jointly optimizes the compactness and direction consistency of features.
- Experiments demonstrate that the proposed method, embedded as a plugin into the mainstream MAR baseline improves the Action Top-1 accuracy of MMN under modality B to 58.74 % and raises the F1 mean of MANet to 66.05 %, significantly enhancing the overall performance of MAR baseline models.

## 💡Installation

```
git clone https: https://github.com/WeiRoBotAI/MGSD-VC.git
cd MGSD-VC
```

```
conda create -n MGSD-VC python=3.12 -y
conda activate MGSD-VC

pip install torch  # cuda version
# pip3 install --pre torch --index-url https://download.pytorch.org/whl/nightly/cu129

pip install scikit-learn tensorboardX timm chardet h5py
pip install -e ./torchlight
pip install -e ./torchpack
```

## Training & Testing

**Dataset (MA-52**）

The dataset can be obtained from the MMN model repository:  [here]([momiji-bit/MMN: [ACM MM 2025\] This repository is the official implementation of the paper "Motion Matters: Motion-guided Modulation Network for Skeleton-based Micro-Action Recognition".](https://github.com/momiji-bit/MMN))

**Pretrain Model**

- Download Link: 

**Training**

```
python main.py --config ./config/train/MA52_J.yaml
python main.py --config ./config/train/MA52_B.yaml
```

**Testing**

```
python test.py --config ./config/test/MA52_J.yaml --weights ./path_to_trained_model.pt
python test.py --config ./config/test/MA52_B.yaml --weights ./path_to_trained_model.pt
python test.py --merge ./work_dir/test/MA52_J ./work_dir/test/MA52_B --work-dir ./work_dir/test/MA52_2s
```

- **MA-52**: Please submit your test prediction files to the Codabench evaluation server competition page: [here](https://www.codabench.org/competitions/9066/)

## 🤝 Acknowledgement



This code began with [MMN](https://github.com/momiji-bit/MMN.git). We thank the developers for doing most of the heavy-lifting.