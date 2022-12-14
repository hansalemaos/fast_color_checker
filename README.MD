### A couple of fast algorithms for counting and locating colors in pictures

#### Get all coordinates of a certain color in your picture

```python
$pip install fast-color-checker  
from fast_color_checker import ColorCheck
```

```python
pic = ColorCheck(r"https://www.python.org/static/opengraph-icon-200x200.png")
x0, y0, xy0 = pic.get_coords_of_color((255, 212, 59))

x0
Out[4]:
array([164, 162, 163, 164, 161, 162, 163, 159, 160, 161, 162, 163, 158,
	   159, 160, 161, 162, 157, 158, 159, 160, 161, 162, 155, 156, 157,
	   158, 159, 160, 161, 154, 155, 156, 157, 158, 159, 160, 161, 152,
	   153, 154, 155, 156, 157, 158, 159, 160, 151, 152, 153, 154, 155,
	   156, 157, 158, 159, 160, 149, 150, 151, 152, 153, 154, 155, 156,
	   ....

y0
Out[7]:
array([117, 118, 118, 118, 119, 119, 119, 120, 120, 120, 120, 120, 121,
	   121, 121, 121, 121, 122, 122, 122, 122, 122, 122, 123, 123, 123,
	   123, 123, 123, 123, 124, 124, 124, 124, 124, 124, 124, 124, 125,
	   125, 125, 125, 125, 125, 125, 125, 125, 126, 126, 126
	   ....

xy0
Out[9]: (if zipxy is True) / (None if zipxy is False)
((164, 117),
 (162, 118),
 (163, 118),
 (164, 118),
 (161, 119),
 (162, 119),
 (163, 119),
 (159, 120),
 (160, 120),
 (161, 120),
 (162, 120),
 (163, 120),
 ....

	Parameters:
		color:Union[str,tuple,list]
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black
		zipxy: bool
			[50,100,200], [20,120,220] -> [(50,20), (100,120), (200,220)]
			(default=True)
		highlightcolor:Union[None,tuple]=None
			Only relevant if you want to see the output results with pic.show_result()
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black
			(default=None)
	Returns:
		tuple
		(all x coordinates, all y coordinates, zipped x,y coordinates/None)
```

#### Get all coordinates of a certain color range in your picture

```python
pic = ColorCheck(r"https://www.python.org/static/opengraph-icon-200x200.png")

each_color_detailed1,sum_1=pic.get_coords_of_color_range(start=(255,215,60),end=  '#FFE262',highlightcolor=(255,0,255))
#result https://github.com/hansalemaos/screenshots/raw/main/colorfind2.png

each_color_detailed1
....
  ((255, 210, 60), ()),
  ((255, 211, 55), ()),
  ((255, 211, 56), ()),
  ((255, 211, 57), ()),
  ((255, 211, 58), ()),
  ((255, 211, 59), ()),
  ((255, 211, 60), ()),
  ((255, 212, 55), ()),
  ((255, 212, 56), ()),
  ((255, 212, 57), ()),
  ((255, 212, 58), ()),
  ((255, 212, 59),
   ((164, 117),
	(162, 118),
	(163, 118),
	(164, 118),
	(161, 119),
	(162, 119),
	(163, 119),
	(159, 120),
	(160, 120),
	(161, 120),
	(162, 120),
	(163, 120),
....

sum1
...
 (132, 125),
 (130, 126),
 (131, 126),
 (129, 127),
 (130, 127),
 (128, 128),
 (126, 129),
 (127, 129),
 (125, 130),
 (123, 131),
 (124, 131),
 (115, 137),
 (113, 138),
 (114, 138),
 (112, 139),
 (110, 140),
 (111, 140),
 ...

	Parameters:
		start:Union[str,tuple,list]
			start of the color range
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black
		end:Union[str,tuple,list]
			end of the color range
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black
		highlightcolor:Union[None,tuple]=None
			Only relevant if you want to see the output results with pic.show_result()
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black
			(default=None)
	Returns:
		tuple
		(all x coordinates, all y coordinates, zipped x,y coordinates/None)
```

#### Count how often a certain color is present

```python
Count how often a certain color is present
pic = ColorCheck(r"https://www.python.org/static/opengraph-icon-200x200.png")

pic.count_color((255, 212, 59))
Out[12]: 477
	Parameters:
		color:Union[str,tuple,list]
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black

	Returns:
		int
```

#### Count how often the colors of a certain color range are present

```python
Count how often the colors of a certain color range are present
pic = ColorCheck(r"https://www.python.org/static/opengraph-icon-200x200.png")
each_color_detailed, sum_ = pic.count_color_range(start=(255, 215, 60), end="FFE262")

sum_
Out[5]: 2976

each_color_detailed
Out[6]:
[((255, 215, 60), 0),
 ((255, 215, 61), 0),
 ((255, 215, 62), 0),
 ((255, 215, 63), 0),
 ((255, 215, 64), 0),
 ((255, 215, 65), 0),
 ((255, 215, 66), 48),
 ((255, 215, 67), 69),
 ((255, 215, 68), 87),
 ((255, 215, 69), 19),
 ...

	Parameters:
		start:Union[str,tuple,list]
			start of the color range
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black
		end:Union[str,tuple,list]
			end of the color range
			examples of valid inputs: (255, 212, 59), ffa7d7, #ffa9d9, black

	Returns:
		tuple
```

#### Get all colors in an image

```python
pic = ColorCheck(r"https://www.python.org/static/opengraph-icon-200x200.png")
pic.get_all_colors_in_image()
((0, 0, 0),
 (77, 64, 18),
 (80, 66, 18),
 (83, 69, 20),
 (86, 72, 20),
 (87, 72, 20),
 (88, 73, 20),
 (77, 66, 21),
 (73, 63, 23),
 (81, 70, 26),
 (118, 98, 27),
 ...
```

#### Count all colors

```python
pic.count_all_colors()
Out[4]:
[((0, 0, 0), 27515),
 ((77, 64, 18), 1),
 ((80, 66, 18), 1),
 ((83, 69, 20), 1),
 ((86, 72, 20), 1),
 ((87, 72, 20), 1),
 ((88, 73, 20), 1),
 ((77, 66, 21), 1),
 ...
```

#### Limit search region

```python
Limit search to a certain region of the picture

pic = ColorCheck(r"https://www.python.org/static/opengraph-icon-200x200.png")

pic.crop_imageselection((100, 100), (150, 150))

each_color_detailed1, sum_1 = pic.get_coords_of_color_range(
	start=(255, 215, 60), end="#FFE262", highlightcolor=(255, 0, 255)
)

pic.reset_cropped_imageselection()

x1, y1, xy1 = pic.get_coords_of_color(
	(255, 212, 59), zipxy=False, highlightcolor=(255, 0, 0)
)

pic.show_result()

#result: https://github.com/hansalemaos/screenshots/raw/main/colorfind4.png

	Parameters:
		start: tuple
			x,y coordinates
		end: tuple
			x,y coordinates
	Returns:
		self
```

#### Reset limited search region

```python
pic.reset_cropped_imageselection()
```

#### Show results

```python
pic.show_result()
Show results
	Parameters:
		window_name: str
			OpenCV window title
			(default = "")
		quit_key: str
			Key to close OpenCV window
			(default = "q")
	Returns:
		self
```
