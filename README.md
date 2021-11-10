# EasyEditor
#создай тут фоторедактор Easy Editor!
import os
from PyQt5.QtWidgets import (QApplication, QLabel, QListWidget, QWidget, QHBoxLayout, QVBoxLayout, QRadioButton)

from PyQt5.QtCore import Qt
from PyQt5.QtGui import QPixmap

from PIL import Image
from PIL.ImageQt import ImageQt
from PIL import ImageFilter
from PIL.ImageFilter import (
    BLUR, CONTOUR, DETAIL, EDGE_ENHANCE, EDGE_ENHANCE_MORE,
    EMBOSS, FIND_EDGES, SMOOTH, SMOOTH_MORE, SHARPEN,
    GaussianBlur, UnsharpMask
)

app = QApplication([])
win = QWidget()
win.resize(700, 500)
win.setWindowTitle('Easy Editor')
lb_image = QLabel("Картинка")
btn_dir = QPushButton("Папка")
lw_files = QListWidget()

btn_folder = QPushButton('Папка')
btn_flip = QPushButton('Зеркало')
btn_left = QPushButton('Лево')
btn_right = QPushButton('Право')
btn_sharp = QPushButton('Резкость')
btn_bw = QPushButton('Ч/Б')

row = QHBoxLayout()
col1 = QVBoxLayout()
col2 = QVBoxLayout()
col1.addWidget(btn_dir)
col1.addWidget(lw_files)
col2.addWidget(lb_image, 95)
row_tools = QHBoxLayout()
row_tools.addWidget(btn_left)
row_tools.addWidget(btn_right)
row_tools.addWidget(btn_flip)
row_tools.addWidget(btn_sharp)
row_tools.addWidget(btn_bw)
col2.addLayout(row_tools)

row.addLoyout(col1, 20)
row.addLoyout(col2, 80)
win.setLoyout(row)

win.show()
workdir = ""


class ImageProcessor():
    def __init__(self):
        self.image = None
        self.dir = None
        self filename = None 
        self.save_dir = "Modified/"
