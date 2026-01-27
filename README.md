# Vector-Database-USAI-CCA-2026
---
##  🤖 Install and Set Up Env For  Unlearn Model 

### 🐍 Create Conda Environment 
- Python **3.6.9** and Create Conda Environment
```
conda create -n bitnet-unlearn-env python=3.6.9 -y
conda activate bitnet-unlearn-env 
```
- Add Virtual Environment to Jupyter Notebook
```
pip install --user ipykernel
python -m ipykernel install --user --name=bitnet-unlearn-env 
```

## 📦 Required Packages

Key libraries and versions:

| Package | Version |
|------|--------|
| tensorflow | 2.6.0rc0 |
| keras | 2.6.0rc0 |
| numpy | 1.19.5 |
| scipy | 1.4.1 |
| pandas | 1.1.5 |
| matplotlib | 3.3.4 |
| opencv-python | 4.6.0.66 |
| scikit-learn | 0.23.0 |
| torch | 1.10.1 |
| torchvision | 0.11.2 |
| scikit-image | 0.17.2 |
| Pillow | 8.4.0 |

```
pip install \
tensorflow==2.6.0rc0 \
keras==2.6.0rc0 \
numpy==1.19.5 \
scipy==1.4.1 \
pandas==1.1.5 \
matplotlib==3.3.4 \
opencv-python==4.6.0.66 \
scikit-learn==0.23.0 \
torch==1.10.1 \
torchvision==0.11.2 \
scikit-image==0.17.2 \
Pillow==8.4.0
```


---
### Install and Setup Env For Pinecone Database
```
conda create -n pinecone_env python=3.9 -y
conda activate pinecone_env
pip install "pinecone[grpc]" 
pip install pandas 
pip install numpy
pip install tqdm
pip install jupyter ipykernel
python -m ipykernel install --user --name pinecone_env --display-name "Python 3.9 (Pinecone_New)"
```
### API Key กับ HOST ให้ไปสร้างที่ Web ของ Pinecone (อันนี้สร้างไว้สำหรับเก็บ Feature Vector ของ CCA Effnet)
```
API_KEY = pcsk_Hyuv6_M238p81iBu75rdPVhogLx1fxYcuqP2YSuNAXBKhvJgJnQXR8CTWczGz1TFU3cuj
INDEX_HOST = https://usai-effnet-features-kbyt94f.svc.aped-4627-b74a.pinecone.io
```
### For Check
```
from pinecone import Pinecone
import pandas as pd

# 1. ตั้งค่าข้อมูลการเชื่อมต่อ
API_KEY = "ใส่_API_KEY_"
INDEX_HOST = "ใส่_HOST_"

try:
    # 2. เริ่มต้นการเชื่อมต่อ
    pc = Pinecone(api_key=API_KEY)
    index = pc.Index(host=INDEX_HOST)
    
    # 3. ทดลองเรียกดูสถิติของ Database
    stats = index.describe_index_stats()
    
    print("✅ [Status] เชื่อมต่อสำเร็จ!")
    print("-" * 30)
    print(f"Dimension ในระบบ: {stats['dimension']}")
    print(f"จำนวนข้อมูลปัจจุบัน (Total Records): {stats['total_vector_count']}")
    print("-" * 30)

except Exception as e:
    print("❌ [Status] การเชื่อมต่อล้มเหลว!")
    print(f"Error: {e}")
```

---
