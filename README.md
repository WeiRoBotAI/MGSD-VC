



## Installation

```
git clone https:
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

```
pip install -U huggingface_hub
huggingface-cli login
# export HF_ENDPOINT=https://hf-mirror.com  # (Optional) For users in China, enable the mirror
huggingface-cli download Geo2425/MMN --repo-type dataset --local-dir data
```

**Pretrain Model**

- Download Link: [here](https://drive.google.com/drive/folders/15yubRV4BOQ18QqFNbB2w6ui30S_UtM7W?usp=sharing)

**Training**

```
python main.py --config ./config/train/MA52_J.yaml
python main.py --config ./config/train/MA52_B.yaml
```

**Testing**

```
# Micro-Action 52 Dataset
python test.py --config ./config/test/MA52_J.yaml --weights ./path_to_trained_model.pt
python test.py --config ./config/test/MA52_B.yaml --weights ./path_to_trained_model.pt
python test.py --merge ./work_dir/test/MA52_J ./work_dir/test/MA52_B --work-dir ./work_dir/test/MA52_2s
```

- **MA-52**: Please submit your test prediction files to the Codabench evaluation server competition page: [here](https://www.codabench.org/competitions/9066/)