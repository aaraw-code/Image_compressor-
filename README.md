# Image_compressor-
Compress the size (MB) of image and convert into a pdf

import os
from PIL import Image

print("--------Welcomr to IMAGE COMPRESSOR--------")

image_path = input("Enter the path of image (eg. JPG,PNG,JPEG): ")

if not os.path.exists(image_path):
    print("File was not found. please check the path and try again!")

else:
    original_size = os.path.getsize(image_path) / (1024 * 1024)                         # its to calculate the size of img
    img = Image.open(image_path)

    if img.mode == "RGBA":
        img= img.convert("RGB")         

    output_pdf = input("Enter the name of new file (do not include = .pdf): ")
    new_pdf = output_pdf + ".pdf"

    img.save(new_pdf, "PDF" )
    pdf_size = os.path.getsize(new_pdf) / (1024 * 1024)

    print("Conversion Complete")
    print(f"Original image size : {original_size:.2f} MB")                            # .2f used for taking only two digits from point (eg = 3.14 , 6.89)
    print(f"New image size : {pdf_size:.2f} MB")
    print(f"Saved as : {new_pdf}")
