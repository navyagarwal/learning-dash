# Dash Fundamentals

💖 Plotly + Flask Lovechild => Dash

### Boilerplate code to build and launch a Dash App

```
from dash import Dash, html

app = Dash(__name__)

app.layout = html.Div([
    html.Div(children='Hello World')
])

if __name__ == '__main__':
    app.run(debug=True)
```

#### ✨ Connecting to Data:

The most common way is to use Pandas to import csv files. We can also use APIs, external databases, local .txt files, JSON files, and more. If you are connecting to a specific database type or file format, use a suitable Python library and refer to its documentation.


#### ✨ App Layout:

The layout of a Dash app describes what the app looks like. The layout is a hierarchical tree of components.

Dash HTML Components (dash.html) provides classes for all of the HTML tags and the keyword arguments describe the HTML attributes like style, class, and id. Dash Core Components (dash.dcc) generates higher-level components like controls and graphs.

#### ✨ Visualizing Data:

We import the dcc module (Dash Core Components). It includes a component called Graph. Graph renders interactive data visualizations using  plotly.js graphing library. The figure argument in the Graph component is the same figure argument that is used by plotly.py, Plotly's open source Python graphing library. We also import the plotly.express library to build the interactive graphs.


#### ✨ Controls and Callbacks: 

Import the callback module and the two arguments commonly used within the callback: Output and Input.


#### ✨ Styling the App:

There are 4 ways to style your Dash Apps:
1. HTML and CSS: CSS styles can be applied within components via the style property, or they can be defined as a separate CSS file in reference with the className property.
2. Dash Design Kit (DDK): Dash Design Kit is licensed as part of Dash Enterprise. It is a high level UI framework that is purpose-built for Dash.
3. Dash Bootstrap Components: Dash Bootstrap is a community-maintained library built off of the bootstrap component system. 
4. Dash Mantine Components: Dash Mantine is a community-maintained library built off of the Mantine component system. It uses the Grid module to structure the layout.


--------------


## References
1. [Dash Plotly Documentation](https://dash.plotly.com/)