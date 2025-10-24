HyperspacePirate on youtube made a janky CT scanner, and I saw that the individual X-ray images looked really sharp, but the final 3-D printed model was terrible. I got severely nerd sniped and 
extracted the X-ray images from the youtube and re-ran the 3-D reconstruction. I got deep into the weeds in compressed-sensing, and ended up doing the whole thing using torch's gradient descent instead of the usual radon-transform
approach. The final model is really detailed!

If you just want the nrrd of the rat, it's here: https://github.com/HastingsGreer/HyperspacePirateCT/releases/tag/0.00001

The basic meme is that modern computers are stupidly powerful (or at least mine is lol, you need a 20GB GPU to run this and it no joke does about .9 quadrillion multiply-adds to do a full quality render, over the course of an hour) so there is no need for any of the old school cleverness with FFTs. As a result, I'm not married to the optimization problem being quadratic- instead, it's all absolute error all the time. This makes it super robust to the shot noise from HyperspacePirate irradiating his poor camera, and puts a strong total variation prior over the image, which crisply resolves the ambiguity from computing a 500x500x500 volume from only 100 projections. This approach also simultaneously solves the volume and the projection transform, so the alignment is perfect.


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

<img width="1062" height="834" alt="image" src="https://github.com/user-attachments/assets/fc080fbc-f3a5-4f45-98e7-da392ec3f8ed" />


