## PCA notebook with Interactive 3D and 2D images

A note to the notebook PCA_Armadillo 3D.ipynb. To get the interactive 3D and 2D 
images of Armadilio add the line

**%matplotlib notebook**

Then, by moving the mouse over the image you will get coodinates (x, y, z) 
for the case _Armadillo 3D_, and (x, y) for 2D projections (blue and red) of Armadillo. 

## PlyData and PlyElement

The var __plyfile__ is of type:  <class 'plyfile.PlyData'>, 
and var __plyfile['vertex']__ is of type <class 'plyfile.PlyElement'>.
The are defined [here](https://github.com/dranjan/python-plyfile/blob/master/plyfile.py).
Vars __plyfile['vertex]['x']__,  __plyfile['vertex]['y']__ and __plyfile['vertex]['z']__
are of type <class 'numpy.ndarray'> having shape (172974,), i.e. we have 3 arrays of
length 172974 bytes. For _reduce_factor = 100_, we get 1730 elements in the reduced arrays,
the result image [Armadilio_1730points.png](https://github.com/Rafael1s/Python-Data-Science-edX/blob/master/PCA_and_RandomizedPCA/images/Armadilio_1730points.png).  For _reduce_factor = 10_, 
we get 17298 elements in the reduced arrays, he result image 
[Armadilio_17298points.png](https://github.com/Rafael1s/Python-Data-Science-edX/blob/master/PCA_and_RandomizedPCA/images/Armadilio_17298points.png).

The _r = reduce_factor_ in the expression with the double colon [::r] 
means the format [_start_:_end_:_step_], where _start_ and _end_ have the defualt values.
