# Integrate Plotly Dash Into Flask App

Flask is a minimalist, generic web framework written in Python.

Dash is data dashboarding tool built on top of Flask.

Thus, every time we make a Dash app, we're actually creating a Flask app with extra bells and whistles. The moment Dash is initialized with `app = Dash(__name__)`, it spins up a Flask app to piggyback off of. The syntax for starting a Dash app is precisely the same as starting a Flask app.

### Creating a fully-featured app, where data visualization is simply a feature of said app
A common workaround is passing Flask to Dash as the underlying "server".

```
from flask import Flask
from dash import Dash, html, dcc

server = Flask(__name__)
app = Dash(__name__, server=server, url_base_pathname='/dash')

app.layout = html.Div(id='dash-container')

@server.route("/dash")
def my_dash_app():
    return app.index()
```

But this method sucks ~

1. Your app will always start on a Dash-served page. We'll want our start page to be something we have full control over to then dive into the Dash components.
2. Access to globally available Flask plugins is still unavailable in this method.
3. Ability to style application with static assets and styles is entirely out of hands.
4. Container architecture built on Flask, such as Google App Engine, won't play nicely when we start something that isn't Flask. So there's a good chance that playing by the rules means losing the ability to deploy.

If we want to do these things, we cannot start our app as an instance of Dash and attempt to work around it. Instead, we must create a Flask app, and put Dash in its place as an app embedded in our app. This gives us full control over when users can enter the Dash interface, and even within that interface, we can still manage database connections or user sessions as we see fit.


------------------

## References
1. https://hackersandslackers.com/plotly-dash-with-flask/