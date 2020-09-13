.. _dict:

Dictionary
==========

มาถึงบทนี้เราสามารถเก็บข้อมูลหลายๆตัวไว้ในตัวแปรเดียวได้
ทำให้การเข้าถึงทำได้ง่าย นั่นคือการใช้ list, tuple, หรือ set

แต่ถ้าข้อมูลแต่ละตัวที่เราจะเก็บนั้นมีลักษณะพิเศษ เช่น ...

การเก็บข้อมูลสมุดโทรศัพท์
ซึ่งจะเก็บชื่อและเบอร์โทรศัพท์ที่คู่กับชื่อนั้น เราอาจใช้ list
ในการเก็บข้อมูลทั้งสอง คือ - List ตัวแรก ใช้ในการเก็บชื่อ - List
ตัวที่สอง ใช้ในการเก็บเบอร์โทรศัพท์

.. code:: 

    names = ['Dan','Beam','Big']
    phonebook = ['086-123-4567','092-987-6543', '083−333-3333']

แล้วถ้า Beam มี 2 เบอร์ล่ะ ... ไม่มีปัญหา ก็ใช้ List มาเก็บข้อมูลของ
Beam ก็ได้ ดัง code ด้านล่าง

.. code:: 

    name_list = ['Dan','Beam','Big']
    phonebook = ['086-123-4567',['092-987-6543','091-234-4567'], '083−333-3333']

ดูเหมือนไม่มีปัญหาอะไร แต่ลองคิดต่อว่าถ้าเราอยากจะโทรไปหา Big
เราต้องหาก่อนว่าเบอร์ของ Big เก็บไว้เป็นลำดับที่เท่าไหร่
เราถึงจะดึงข้อมูลออกมาได้ ซึ่งสามารถเขียนโปรแกรมได้ดังนี้

.. code:: 

    for i in range(len(name_list)):
      if name_list[i] == 'Big':
        print(phonebook[i])

ลองจินตนาการต่อว่าถ้า phonebook ของเราเล่มใหญ่มาก
เก็บรายชื่อและเบอร์โทรศัพท์ของงคนทั้งประเทศ ถ้าเราอยากจะโทรหาใครซักคน
เราต้องวนลูปไปนานมากกว่าจะได้เบอร์ของคนนั้นมา ทำให้เสียเวลามาก

ดังนั้นใน Python จึงมีการเก็บข้อมูลแบบกลุ่มอีกแบบหนึ่ง เรียกว่า
Dictionary หรือเรียกย่อๆว่า Dict
ที่จะทำให้การเข้าถึงข้อมูลในลักษณะแบบที่เป็นคู่กัน เช่น
ชื่อกับเบอร์โทรศัพท์ ได้ง่ายและรวดเร็ว

สิ่งที่ Dict ทำก็คือ การอนุญาตให้ผู้ใช้สามารถตั้งชื่อ index ได้เอง
(เรียกว่า key)
โดยที่ไม่จำเป็นต้องเป็นตัวเลขจำนวนเต็มที่เรียงกันเป็นลำดับเหมือนที่ใช้ในลิสต์

รูปแบบของ dict
--------------

-  dict เก็บข้อมูลเป็นคู่ ๆ ในลักษณะของ key :math:`\rightarrow` value
-  เขียนสมาชิกภายใน วงเล็บปีกกา { }
-  สมาชิกแต่ละตัวคั่นดด้วย จุลภาค ,
-  key กับ value คั้นด้วย :

.. code:: python

    {คีย์ตัวที่ 1: ข้อมูลคู่กับคีย์ตัวที่ 1, คีย์ตัวที่ 2: ข้อมูลคู่กับคีย์ตัวที่ 2, ..., คีย์n: ข้อมูลคู่กับคีย์ตัวที่ n}

ดังนั้น เราสามารถสร้าง dict เพื่อเก็บเบอร์โทรศัพท์ ของ Dan, Beam, Big
ได้ดังนี้

.. code:: 

    phonebook = {'Dan': '086-123-4567', 'Beam': ['092-987-6543','091-234-4567'], 'Big':'083−333-3333'}

จะเห็นว่าเราใช้ dict แค่อันเดียว แทนการใช้ list สองอันในการเก็บข้อมูล

.. code:: 

    phonebook




.. parsed-literal::

    {'Beam': ['092-987-6543', '091-234-4567'],
     'Big': '083−333-3333',
     'Dan': '086-123-4567'}



Note: Dict ไม่มีลำดับ !!

\ **Q:**\  ลองวาดตารางของ key กับ value ของตัวอย่างด้านล่าง

.. code:: 

    subject_id = '2301170'
    subject = 'Python' 
    days = ['M','W','F'] 
    data = {'First': [1, 2, 3], True: 8, -2.5: (4, '5'), (0,'k'): False, 'last':{},subject_id: subject, 'class':days}

**Ans:** Click to expand >>

\| KEY \| VALUE \| \| --- \| --- \| \| 'First' \| [1,2,3] \| \| True \|
8 \| \| -2.5 \| (4,5) \| \|(0,'k')\| False \| \| 'last' \| {} \| \|
'2301170' \| 'Python'\| \| 'class' \| ['M','W','F']

\ **Q:**\  ลำดับข้อมูลใน dict เป็นไปตามที่เราใส่ข้อมูลมั๊ย?

.. code:: 

    data # จะเห็นว่า dict ไม่มีลำดับ




.. parsed-literal::

    {(0, 'k'): False,
     -2.5: (4, '5'),
     '2301170': 'Python',
     'First': [1, 2, 3],
     True: 8,
     'class': ['M', 'W', 'F'],
     'last': {}}



Notes \* ประเภทข้อมูลที่ใช้เป็น Key จะเป็นข้อมูลประเภทอะไรก็ได้ i.e.
string, int, float, boolean, หรือแม้กระทั่ง tuple แต่ \ **ยกเว้น**\ 
list กับ dict. \* ประเภทข้อมูลที่ใช้เป็น Value เป็นอะไรก็ได้ i.e.
string, int, float, boolean, tuple, list, dict

การเข้าถึงข้อมูลใน dict
-----------------------

เนื่องจากลำดับของข้อมูลใน dict ไม่เหมือนกับลำดับที่เราใส่ข้อมูลเข้าไป
ดังนั้น dict ไม่เหมือนกับ list หรือ tuple จึงไม่สามารถเข้าถึงข้อมูลด้วย
index

แต่เราสามารถเข้าถึงข้อมูล (value) ใน dict ด้วย key

.. code:: python

    ตัวแปรดิก[คีย์ที่ต้องการ]

.. code:: 

    phonebook['Beam']




.. parsed-literal::

    ['092-987-6543', '091-234-4567']



.. code:: 

    phonebook['Dan']




.. parsed-literal::

    '086-123-4567'



.. code:: 

    phonebook['dan'] #จะเกิด error หรือไม่ เพราะอะไร (Hint: case sensitive)


::


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-44-c04e21372b64> in <module>()
    ----> 1 phonebook['dan'] #จะเกิด error หรือไม่ เพราะอะไร (Hint: case sensitive)
    

    KeyError: 'dan'


.. code:: 

    phonebook['Big']




.. parsed-literal::

    '083−333-3333'



.. code:: 

    phonebook['the toy']


::


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-46-00dfefc60030> in <module>()
    ----> 1 phonebook['the toy']
    

    KeyError: 'the toy'


--------------

.. code:: 

    data[(0,'k')]




.. parsed-literal::

    False



.. code:: 

    data[-2.5]




.. parsed-literal::

    (4, 5)



.. code:: 

    data[subject_id]




.. parsed-literal::

    'Python'



.. code:: 

    data['2301170']




.. parsed-literal::

    'Python'



.. code:: 

    data['First']




.. parsed-literal::

    [1, 2, 3]



.. code:: 

    data[True]




.. parsed-literal::

    8



.. code:: 

    data['class']




.. parsed-literal::

    ['M', 'W', 'F']



.. code:: 

    data['last']




.. parsed-literal::

    {}



การเข้าถึงสมาชิกทุกตัวใน dict
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: 

    for k in phonebook:
      # แสดงผล key และ value เป็นคู่ ๆ
      print(k, ':',phonebook[k])

--------------

.. code:: 

    for k in data:
      # แสดงผล key และ value เป็นคู่ ๆ
      print(k,':', data[k])


.. parsed-literal::

    First : [1, 2, 3]
    True : 8
    -2.5 : (4, 5)
    (0, 'k') : False
    last : {}
    2301170 : Python
    class : ['M', 'W', 'F']


\ **Q:**\  ลองเขียนโปรเเกรมเพื่อให้แสดงผลว่าเบอร์ '086-123-4567'
เป็นเบอร์ของใคร

.. code:: 

    phonebook['086-123-4567'] # ได้มั๊ย?


::


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-28-1f41008f6ab0> in <module>()
    ----> 1 phonebook['086-123-4567'] # ได้มั๊ย?
    

    KeyError: '086-123-4567'


.. code:: 

    # Code here

การเก็บข้อมูลของ Dict
---------------------

.. code:: 

    data




.. parsed-literal::

    {(0, 'k'): False,
     -2.5: (4, 5),
     '2301170': 'Python',
     'First': [1, 2, 3],
     True: 8,
     'class': ['M', 'W', 'F'],
     'last': {}}





--------------

.. code:: 

    phonebook




.. parsed-literal::

    {'Beam': ['092-987-6543', '091-234-4567'],
     'Big': '083−333-3333',
     'Dan': '086-123-4567'}





การเปลี่ยนแปลงข้อมูลใน dict
---------------------------

-  **เพิ่มข้อมูลใหม่ / การปรับปรุงค่าใน dict**

.. code:: python

    ตัวแปรดิก[คีย์] = ค่า

.. code:: 

    phonebook[('bodyslam',1)] = '121-231-2121'



.. code:: 

    print('Before', phonebook['Dan'])
    phonebook['Dan'] = '085-555-5555'
    print('After',phonebook['Dan'])



Notes

-  dict ไม่สามารถมี key ซ้ำได้
-  สิ่งที่เกิดขึ้นเมื่อเราใส่ข้อมูล (value) ใหม่ลงไปใน dict โดยใช้ key
   ที่มีอยู่แล้ว คือ จะเป็นการเขียน value ทับค่าเดิมทันที

-  **ลบข้อมูล**

.. code:: python

    del ดิก[คีย์]

.. code:: 

    del phonebook['Big']



.. code:: 

    del phonebook['the toy']


::


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-31-a84b90d22ce2> in <module>()
    ----> 1 del phonebook['the toy']
    

    KeyError: 'the toy'


การสร้าง dict
-------------

\ **Q:**\  ลองสร้าง dict ที่มีข้อมูลดังตารางข้างล่าง

+--------------------------+--------------------------+
| KEY                      | VALUE                    |
+==========================+==========================+
| 'model'                  | 'Cooper S'               |
+--------------------------+--------------------------+
| 'year'                   | 2020                     |
+--------------------------+--------------------------+
| 'fuel tank'              | 11.6                     |
+--------------------------+--------------------------+
| 'dimension'              | (152.5,68,55.7)          |
+--------------------------+--------------------------+
| ('contact','Thailand')   | 'callcenter@bmw.co.th'   |
+--------------------------+--------------------------+

วิธีที่ 1: สร้างทีเดียว

.. code:: 

    mini = {'model':'Cooper S','year':2020,'fuel tank':11.6,'dimension':(152.5,68,55.7),('contact','Thailand'):'callcenter@bmw.co.th'}

วิธีที่ 2: สร้างจาก dict เปล่า แล้วค่อยๆเติมของลงไป

.. code:: 

    # สร้าง dict เปล่า มี 2 แบบให้เลือก
    mini = {} 
    # mini = dict()
    
    # เติมของ
    mini['model'] = 'Cooper S'
    mini['year'] = 2020
    mini['fuel tank'] = 11.6
    mini['dimension'] = (152.5,68,55.7)
    mini[('contact','Thailand')] = 'callcenter@bmw.co.th'

P: เขียนโปรแกรมเพื่ออ่านไฟล์ genome.csv แล้วนำมาสร้างเป็น dict
โดยใช้ข้อมูลตัวแรกเป็น Key และข้อมูลตัวที่สองเป็นต้นไปเป็น Value

.. code:: 

    # Download file


ฟังก์ชันที่ควรรู้ของ dict
-------------------------

``update`` การปรับปรุงค่าใน dict ด้วย dict อีกอัน
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    ดิกตัวแรก.update(ดิกตัวที่สอง)

.. code:: 

    phonebook_inter = {'Blackpink':(),'Dan':()}

image

``keys`` การเข้าถึงข้อมูลที่เป็นคีย์ทุกตัวใน dict
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    ดิก.keys() 

.. code:: 

    phonebook.keys()




.. parsed-literal::

    dict_keys(['Dan', 'Beam', 'Big'])



.. code:: 

    list(phonebook.keys())




.. parsed-literal::

    'Dan'



.. code:: 

    for key in phonebook.keys():
      print(key)


.. parsed-literal::

    Dan
    Beam
    Big


.. code:: 

    for key in phonebook():
      print(key)

--------------

.. code:: 

    data.keys()

.. code:: 

    for key in data.keys():
      print(key)


.. parsed-literal::

    First
    True
    -2.5
    (0, 'k')
    last
    2301170
    class


.. code:: 

    for key in data:
      print(key)


.. parsed-literal::

    First
    True
    -2.5
    (0, 'k')
    last
    2301170
    class


``values`` *การเข้าถึงข้อมูลที่เป็นข้อมูลทุกตัวใน* dict
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    ดิก.values() 

.. code:: 

    phonebook.values()

.. code:: 

    list(phonebook.values())

.. code:: 

    for val in phonebook.values():
      print(val)

``items`` *การเข้าถึงข้อมูลที่เป็นคีย์และข้อมูลทุกตัวใน* dict
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    ดิก.items() 

.. code:: 

    phonebook.items()




.. parsed-literal::

    dict_items([('Dan', '086-123-4567'), ('Beam', ['092-987-6543', '091-234-4567']), ('Big', '083−333-3333')])



.. code:: 

    list(phonebook.items())

.. code:: 

    for item in phonebook.items():
      print(type(item),item)


.. parsed-literal::

    <class 'tuple'> ('Dan', '086-123-4567')
    <class 'tuple'> ('Beam', ['092-987-6543', '091-234-4567'])
    <class 'tuple'> ('Big', '083−333-3333')


.. code:: 

    for key,val in phonebook.items():
      print(key,'>>>>',val)


.. parsed-literal::

    Dan >>>> 086-123-4567
    Beam >>>> ['092-987-6543', '091-234-4567']
    Big >>>> 083−333-3333


``len`` ฟังก์ชันที่ใช้หาจำนวน items ใน dict
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: python

    len(ดิก) 

.. code:: 

    len(phonebook)




.. parsed-literal::

    3



.. code:: 

    len(data)




.. parsed-literal::

    7



.. code:: 

    len(mini)




.. parsed-literal::

    5



​Dict comprehension
-------------------

คือการสร้างดิก โดยใช้ for ในบรรทัดเดียว เช่นเดียวกับ List comprehension

Pointer
-------

.. code:: 

    x = {3:1}
    a = x 
    a[3] = 3
    a[4] = 4
    a[5] = a[4]
    a[4] = 44
    print('a',id(a),a)
    print('x',id(x),x)


.. parsed-literal::

    a 140352267157080 {3: 3, 4: 44, 5: 4}
    x 140352267157080 {3: 3, 4: 44, 5: 4}


การนับ โดยใช้ dict
------------------

\ **Program:**\  การลงคะแนนเสียงประชามติในวันที่ 7
สิงหาคมนั้นมีคําถามให้ตอบ 2 คําถาม แต่ละคําถามมี 2 คําตอบ คือ Yes หรือ
No นอกจากจะนับคะแนน เสียงของแต่ละคําถามแล้ว
นิสิตอยากหาความสัมพันธ์ของการตอบคําถาม ท้ังสองว่า
มีผลลงคะแนนร้อยละเท่าใดท่ี

.. code:: 

    # Generate input file
    for i in range(100):
      ....
    
    # Code here
    counter = {}
    counter = {'y':0, 'n':0}
    # Open file
    for line in ... :
      # แต่ละบรรทัดเป็นคำตอบจาก 1 คน
      ans1,ans2 = line.split(' ')
      



.. parsed-literal::

    Answer y or n: n
    n


\ **Program:**\  จงนับจํานวนของอักขระ A, B, C, ..., Z ในไฟล์ article.txt
ว่ามีอย่างละก่ีตัว

.. code:: 

    # Code here
    txt = input('Enter text: ').upper()
    
    cnt = {}
    
    # initiate each element in cnt to zero.
      
    # count

Dict 2 มิติ
-----------

สมมติว่าเราจะเก็บข้อมูลตารางด้านล่าง

+---------------+----------+---------+-----------------+-----------+
|               | Credit   | Grade   | Class           | Online?   |
+===============+==========+=========+=================+===========+
| **2301170**   | 3        | 'B+'    | ['M','W','F']   | True      |
+---------------+----------+---------+-----------------+-----------+
| **2301172**   | 1        | 'A'     | ['Thu']         | True      |
+---------------+----------+---------+-----------------+-----------+
| **2301180**   | 2        | 'B'     | '-'             | False     |
+---------------+----------+---------+-----------------+-----------+

เราจะเก็บข้อมูลนี้อย่างไร มีข้อดีข้อเสียอย่างไร

.. code:: 

    # แบบที่ 1
    mycourse = {}
    mycourse['2301170'] = [3,'B+',['M','W','F'],True]
    mycourse['2301172'] = [1,'A',['Thu'],True]
    mycourse['2301191'] = [2,'B','-',False]
    
    print(mycourse['2301172'][2])

.. code:: 

    # แบบที่ 2
    mycourse = {}
    mycourse['2301170'] = {'Credit':3,'Grade':'B+','Online?':True,'Class':['M','W','F']}
    mycourse['2301172'] = {'Credit':1,'Grade':'A','Class':['Thu'],'Online?':True}
    mycourse['2301180'] = {}
    mycourse['2301180']['Class'] = '-'
    mycourse['2301180']['Credit'] = 2
    mycourse['2301180']['Online?'] = 2
    mycourse['2301180']['Grade'] = 'B'
    
    print(mycourse['2301172']['Class'])

\ **Program:**\  เขียนโปรแกรมเพื่ออ่านข้อมูลจากไฟล์ table.csv
และเก็บข้อมูลตารางนี้ให้อยู่ในรูปแบบ Dict สองมิติดังตัวอย่างด้านล่าง

บางส่วนจากไฟล์ table.csv

::

    Course,Credit,Grade
    2301170,3,C+
    2301172,2,A
    2301117,4,B+

Dict ที่ต้องการสร้าง

::

    table['2301170']['Credit'] เก็บค่า 3
    table['2301170']['Grade'] เก็บค่า C+
    table['2301172']['Credit'] เก็บค่า 2
    table['2301172']['Grade'] เก็บค่า A

.. code:: 

    # Code here

Dict หลายมิติ
-------------

Programming exercises
---------------------

1. 

2. 

3. 

4. 

https://erlerobotics.gitbooks.io/erle-robotics-learning-python-gitbook-free/content/lists/exercises\_list\_and\_dictionaries.html
