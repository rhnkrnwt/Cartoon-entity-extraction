# Cartoon-entity-extraction
Run for Garfield comics dataset. Preprocessing involves using PixelAnnotation tool to create training masks. Unet (Pytorch) was run to segment the data on an NVIDIA RTX2070 8GB GPU 

### Installations:
- Python 3.6
- `pip install requirements.txt`
- CUDA 10.2, cuDNN
- Download checkpoint from [here](https://drive.google.com/file/d/12hTF0IpccmdRLE0LZmw-t9qbcQ9juq8O/view?usp=sharing).

### References: 
- Paper: [UNET](https://arxiv.org/abs/1505.04597)
- Github: [milesial/Pytorch-UNet](https://github.com/milesial/Pytorch-UNet)

### Dataset: 
- Annotated using [abreheret/PixelAnnotationTool](https://github.com/abreheret/PixelAnnotationTool) which can be downloaded by doing the following: <pre><code>wget https://github.com/abreheret/PixelAnnotationTool/releases/download/v1.3.1/PixelAnnotationTool_x86_64_v1.3.1.AppImage 
chmod +x PixelAnnotationTool_x86_64_v1.3.1.AppImage
./PixelAnnotationTool_x86_64_v1.3.1.AppImage
</code></pre>
- For training: Under the data folder
- For testing validation: Can be parsed and generated. Used the dataset from [here](https://garfield.dale.ro/) 
- ![Annotated Images example](https://raw.githubusercontent.com/hensden/Cartoon-entity-extraction/master/res/oseg.png)
### Training: 
- Edit data loader and filepaths and run `python3 train.py`

### Running Inference:
<pre><code>src = '/path/to/test_images'
tgt = '/path/to/saved_images'
for image in os.listdir(src): 
    os.system("python predict.py -i " + src + image + " -o " + tgt + image + " --model checkpoints/CP_epoch45.pth") 
</code></pre>

### Results: 
![Garfield](https://raw.githubusercontent.com/hensden/Cartoon-entity-extraction/master/res/garfield.png)  

![Jon](https://raw.githubusercontent.com/hensden/Cartoon-entity-extraction/master/res/jon.png)  

![Bubbles](https://raw.githubusercontent.com/hensden/Cartoon-entity-extraction/master/res/bubble.png)  





