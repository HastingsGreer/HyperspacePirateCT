HyperspacePirate on youtube made a janky CT scanner, and I saw that the individual X-ray images looked really sharp, but the final 3-D printed model was terrible. I got severely nerd sniped and 
extracted the X-ray images from the youtube and re-ran the 3-D reconstruction. I got deep into the weeds in compressed-sensing, and ended up doing the whole thing using torch's gradient descent instead of the usual radon-transform
approach. The final model is really detailed!


How to run:

```
git clone https://github.com/HastingsGreer/HyperspacePirateCT
cd HyperspacePirateCT
python -m venv venv
source venv/bin/activate
pip install torch itk matplotlib scipy jupyter yt-dlp opencv

jupyter notebook
```


<img width="1062" height="834" alt="image" src="https://github.com/user-attachments/assets/8daa8b6f-8c14-4259-bb1b-fdba8eaf2446" />

