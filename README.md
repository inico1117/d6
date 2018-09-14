# d6
#itertools
import itertools
ns=itertools.repeat('A',3)
for n in ns:
    print(n)
    
natuals=itertools.count(1)
ns=itertools.takewhile(lambda x:x<=10,natuals)
list(ns)

#chain()
for c in itertools.chain('XYZ','ABC'):
    print(c)
    
#groupby()
for key,group in itertools.groupby('AAABBBCCAAA'):
    print(key,list(group))
    
for key,group in itertools.groupby('AaaBBbcCAAa',lambda x:x.upper())
    print(key,list(group))
    
#计算圆周率
import itertools
def pi(N):
    ' 计算pi的值 '
    # step 1: 创建一个奇数序列: 1, 3, 5, 7, 9, ...
    natuals=itertools.count(1,2)
    # step 2: 取该序列的前N项: 1, 3, 5, 7, 9, ..., 2*N-1.
    ns=itertools.takewhile(lambda x:x<=2*N,natuals)
    L=list(ns)
    # step 3: 添加正负符号并用4除: 4/1, -4/3, 4/5, -4/7, 4/9, ...
    sum=0
    for i in L:
        sum=sum+(-1)**(i//2)*(4/i)
    # step 4: 求和:
    return sum

#with
class Query(object):

    def __init__(self, name):
        self.name = name
        
    def __enter__(self):
        print('Begin')
        return self
        
    def __exit__(self, exc_type, exc_value, traceback):
        if exc_type:
            print('Error')
        else:
            print('End')
            
    def query(self):
        print('Query info about %s...' % self.name)
        
with Query('Bob') as q:
    q.query()
    
#urllib
from urllib import request
import json
def fetch_data(url):
    with request.urlopen(url) as f:
        return json.loads(f.read())
        
 #Image
 from PIL import Image
 im=Image.open('test.jpg')
 w,h=im.size
 print('Original image size: %s %s' %(w,h))
 im.thumbnail((w//2,h//2))
 print('Resize image to: %s %s' %(w//2,h//2))
 im.save('thumbnail.jpg','jpeg')
 
 from PIL import Image,ImageFiiter
 im=Image.open('test.jpg')
 im2=im.filter(ImageFilter.BLUR)
 im2.save('blur.jpg','jpeg')
 
#code
from PIL import Image,ImageFont,ImageDraw,ImageFilter
import random
 
def rndChar():
    return chr(random.randint(65,90))
def rndColor():
    return (random.randint(64,255),random.randint(64,255),random.randint(64,255))
def rndColor2():
    return (random.randint(32,127),random.randint(32,127),random.randint(32,127))

width=60*4
height=60
image=Image.new('RGB',(width,height),(255,255,255))
font=ImageFont.truetype('simsun.ttf',36)
draw=ImageDraw.Draw(image)
for x in range(width):
    for y in range(height):
        draw.point((x,y),fill=rndColor())
for t in range(4):
    draw.text((60*t+10,10),rndChar(),font=font,fill=rndColor2())
image=image.filter(ImageFilter.BLUR)
image.save('code.jpg','jpeg')
