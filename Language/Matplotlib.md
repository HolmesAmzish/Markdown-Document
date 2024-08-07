# Plotting

## Default X-Points

If we do not specify the points on the x-axis, they will get the default values 0, 1, 2, 3 etc., depending on the length of the y-points.

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10, 5, 7])

plt.plot(ypoints)
plt.show()
```



# Markers

## Format Strings `fmt`

You can also use the *shortcut string notation* parameter to specify the marker.

This parameter is also called `fmt`, and is written with this syntax:

```
*marker*|*line*|*color*
```

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, 'o:r')
plt.show()
```



# Line

## Linestyle

You can use the keyword argument `linestyle`, or shorter `ls`, to change the style of the plotted line:

```python
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, linestyle = 'dotted')
plt.show()
```

## Multiple Lines

```python
import matplotlib.pyplot as plt
import numpy as np

y1 = np.array([3, 8, 1, 10])
y2 = np.array([6, 2, 7, 11])

plt.plot(y1)
plt.plot(y2)

plt.show()
```



# Labels and Title

## Create Labels and Title

You can use the `xlabel()` and `ylabel()` functions to set a label for the x- and y-axis. use the `title()` function to set a title for the plot.

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])

plt.plot(x, y)

# Set the title
plt.title("Sports Watch Data")

# Set labels for x and y axis
plt.xlabel("Average Pulse")
plt.ylabel("Calorie Burnage")

plt.show()
```

## Font Properties

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])

font1 = {'family':'serif','color':'blue','size':20}
font2 = {'family':'serif','color':'darkred','size':15}

plt.title("Sports Watch Data", fontdict = font1)
plt.xlabel("Average Pulse", fontdict = font2)
plt.ylabel("Calorie Burnage", fontdict = font2)

plt.plot(x, y)
plt.show()
```

## Position

```python
plt.title("Sports Watch Data", loc = 'left')
```



# Grid

## Add Grid Lines

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array([80, 85, 90, 95, 100, 105, 110, 115, 120, 125])
y = np.array([240, 250, 260, 270, 280, 290, 300, 310, 320, 330])

plt.title("Sports Watch Data")
plt.xlabel("Average Pulse")
plt.ylabel("Calorie Burnage")

plt.plot(x, y)

# Add the Grid to the plot
plt.grid()

plt.show()
```

## Specify Line

```python
plt.grid(axis = 'x')
```

## Line Properties

```python
plt.grid(color = 'green', linestyle = '--', linewidth = 0.5)
```

# Function

## Sigmoid function

```python
import numpy as np
import matplotlib.pyplot as plt

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

x = np.linspace(-10, 10, 400)

y = sigmoid(x)

plt.plot(x, y)

plt.title("Sigmoid Function")
plt.xlabel("x")
plt.ylabel("sigmoid(x)")

plt.grid(True)

plt.show()
```

