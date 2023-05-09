# Securing Web Forms with Flask-WTF

## Introduction
Web security is crucial in preventing unauthorized access, data breaches, and other harmful activities that can affect users' privacy and data. Unsecured web forms are one of the most common ways for attackers to exploit vulnerabilities in web applications. Flask-WTF is a Flask extension that provides built-in CSRF protection, form validation, and other features to enhance the security of web forms.

## Instructions

To install Flask-WTF, you can use pip by running the command "pip install Flask-WTF". It's important to add Flask-WTF to your requirements file or virtual environment to ensure that your application runs smoothly.

## Creating a Basic Flask Application with Flask-WTF

```
from flask import Flask, render_template
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField

app = Flask(__name__)
app.config['SECRET_KEY'] = 'secretkey'

class NameForm(FlaskForm):
    name = StringField('Name')
    submit = SubmitField('Submit')

@app.route('/', methods=['GET', 'POST'])
def home():
    form = NameForm()
    if form.validate_on_submit():
        name = form.name.data
        return render_template('greeting.html', name=name)
    return render_template('form.html', form=form)

if __name__ == '__main__':
    app.run(debug=True)
```

The provided code defines a simple form that takes a name input and displays a personalized greeting on a new page. FlaskForm provides an easy way to define form fields and handle form validation, while the SECRET_KEY configuration setting is used by Flask-WTF to provide CSRF protection.


## Adding Validation and CSRF Protection to the Form

To validate form data, you can use Flask-WTF's validate_on_submit() method. Flask-WTF can also help protect against common web vulnerabilities like CSRF attacks by using its CSRFProtect() function to add CSRF protection to your form.
