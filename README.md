##  [ [Click here for Scribe Link](https://scribehow.com/shared/SAM2__Phase_1__6U3CDuthRhqFBRnAeain_Q) ]  [ [Click here for Report](https://docs.google.com/document/d/1MqVZUDS_6SSwCbpJZKSYe351H0_Ic0Le0T6BTPweyVQ/pub) ]    [ [Official Paper](https://arxiv.org/pdf/2304.02643) ]



<img width="1266" alt="image" src="https://github.com/user-attachments/assets/cc1c7165-9fc1-4f89-bd3f-80ba75fd7a22">


---

<!--### File Structure
<img width="299" alt="image" src="https://github.com/user-attachments/assets/cc0084da-71c6-4cdb-91ee-babd9ad08f03">-->


#### Download:  
```
!git clone https://github.com/facebookresearch/segment-anything-2.git
%cd {HOME}/segment-anything-2
!pip install -e . -q
```

#### Requirement:

```
!pip install -q supervision jupyter_bbox_widget
```

#### Imports
```
import cv2
import torch
import base64

import numpy as np
import supervision as sv

from sam2.build_sam import build_sam2
from sam2.sam2_image_predictor import SAM2ImagePredictor
from sam2.automatic_mask_generator import SAM2AutomaticMaskGenerator
```

### Available model checkpoints from repo

Name | link | Config file
| ---- | ---- | ---- |
sam2_hiera_tiny.pt | [download pickle](https://huggingface.co/facebook/sam2-hiera-tiny/tree/main) | `sam2_hiera_t.yaml`
sam2_hiera_small.pt | [download pickle](https://huggingface.co/facebook/sam2-hiera-small) | `sam2_hiera_s.yaml`
sam2_hiera_base_plus.pt | [download pickle](https://huggingface.co/facebook/sam2-hiera-base-plus) | `sam2_hiera_b+.yaml`
sam2_hiera_large | [download pickle](https://huggingface.co/facebook/sam2-hiera-large) | `sam2_hiera_l.yaml`

## Speed-Accuracy tradeoff --> optimal = base-plus-ht

| tiny | small | base plus | high |
| ---- | ----- | --------- | ---- |
|      |       | <img width="963" alt="image" src="https://github.com/user-attachments/assets/c996a551-b6f9-4b60-88b9-4cffc49039c2"> | <img width="640" alt="image" src="https://github.com/user-attachments/assets/f486a07e-e2e8-42c2-9a92-957b2390b15f">
|      |       |  | <img width="975" alt="image" src="https://github.com/user-attachments/assets/c1948456-1f6b-4a88-8d04-90033b1844f2">



Problems with grayscale image

<img width="276" alt="image" src="https://github.com/user-attachments/assets/03003402-f0c9-42d0-be91-7f56d5040411">
<img width="216" alt="image" src="https://github.com/user-attachments/assets/25e2946d-e472-4a2d-bc33-99cca06f85d9">
<img width="216" alt="image" src="https://github.com/user-attachments/assets/06ea44ac-78b7-4e04-805b-fe2647e8dc15">


### --> T4 cannot process images of 3000 × 1951 px (1.3MB)
### --> L4 Fails
<img width="1371" alt="image" src="https://github.com/user-attachments/assets/81c7df05-42ca-4335-9731-18287396e58a">

Limit = Under 500kb


<img width="1077" alt="image" src="https://github.com/user-attachments/assets/0bf8b44b-da15-4015-8b05-8c51e675c21f">


Problems with less defines margins

<img width="990" alt="image" src="https://github.com/user-attachments/assets/b84d1253-0251-43ce-ad31-c4dbc060b3c7">







