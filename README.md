# homework2-3

import cv2
import numpy as np

kernel=np.array([[0,0,0], //縦方向の輪郭検出用のカーネル
                 [-1,0,1],
                 [0,0,0]])

capture = cv2.VideoCapture(0)

def edgefilter(x):
    gray=cv2.cvtColor(frame,cv2.COLOR_RGB2GRAY) //グレースケール変換
    y=cv2.filter2D(gray,cv2.CV_64F,kernel)  //cv2.filter2Dメソッドによる輪郭検出
    return y

while(True):
    ret, frame = capture.read()
    cv2.imshow('frame1',frame)  //何も処理してない画像
    cv2.imshow('frame4',edgefilter(frame))  //輪郭検出した画像
    if cv2.waitKey(1) & 0xFF == ord('q'): //qを押したら終了
        break

capture.release()
cv2.destroyAllWindows()





//Python 3.6.6 |Anaconda custom (64-bit)| (default, Jun 28 2018, 11:07:29) 
//[GCC 4.2.1 Compatible Clang 4.0.1 (tags/RELEASE_401/final)] on darwin
//Type "help", "copyright", "credits" or "license" for more information.


//フィルタリングとして輪郭検出を行った.
//参考:https://algorithm.joho.info/programming/python/opencv-differential-filter-py/
