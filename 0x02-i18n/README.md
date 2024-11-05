
# 0x02. i18n - Flask Internationalization

This project aims to teach you how to implement internationalization (i18n) and localization in a Flask web application. You'll learn how to make a web application adaptable to different languages, regions, and time zones, by dynamically displaying content based on user preferences or URL parameters.

The project involves building a basic Flask application with translation support and timezone handling.

## Learning Objectives

By the end of this project, you will have learned how to:

- Parametrize Flask templates to display different languages.
- Determine the user's preferred locale from URL parameters, user settings, or request headers.
- Localize timestamps to display them in the user's local time.
- Use the Flask-Babel extension to manage translations and timezones.

## Project Setup

### Requirements

- **Operating System:** Ubuntu 18.04 LTS or similar.
- **Python Version:** Python 3.7.
- **Dependencies:**
  - `Flask`
  - `Flask-Babel==2.0.0`
  - `pytz`

### Setup Instructions

1. **Install dependencies**:
   To install the required libraries, run the following command in your project directory:

   ```bash
   pip3 install flask_babel==2.0.0 pytz
   ```

2. **Make Python Files Executable**:
   Ensure all your Python files are executable by adding the shebang at the top of each Python script:

   ```python
   #!/usr/bin/env python3
   ```

3. **Code Style**:
   Your code must conform to [PEP 8](https://pep8.org/). Use `pycodestyle` to check the style of your Python code.

4. **Documentation**:
   All modules, classes, and functions should be properly documented with docstrings. Functions must also be type-annotated.

### Files Overview

The following files will be part of your project:

- `0-app.py`: The basic Flask app with a single route and template.
- `1-app.py`: App with Flask-Babel integration.
- `2-app.py`: Adds language detection based on request headers.
- `3-app.py`: Implements template translation using Babel.
- `4-app.py`: Adds support for locale via URL parameters.
- `5-app.py`: Mock login system to emulate user-specific settings.
- `6-app.py`: Uses user settings to determine locale.
- `7-app.py`: Implements timezone support with `pytz`.
- `app.py`: Final app with localized time display.
- `babel.cfg`: Babel configuration file.
- `templates/*`: Jinja2 HTML templates.
- `translations/en/LC_MESSAGES/messages.po`: English translation file.
- `translations/fr/LC_MESSAGES/messages.po`: French translation file.

### Tasks

#### 0. Basic Flask App

- Create a simple Flask app in `0-app.py` with a single route (`/`).
- The template (`0-index.html`) should output "Welcome to Holberton" as the page title and "Hello world!" as the header.

#### 1. Basic Babel Setup

- Install and configure `Flask-Babel` to handle translations.
- Create a `Config` class with available languages `en` and `fr`.
- Set the default locale as `en` and the timezone as `UTC`.
- Update your app to use `Config` for localization.

#### 2. Get Locale from Request

- Implement the `get_locale` function using the `babel.localeselector` decorator to detect the best language match based on `request.accept_languages`.

#### 3. Parametrize Templates

- Use `gettext` to parametrize templates.
- Extract and initialize translation files using `pybabel` commands.
- Provide translations for the `home_title` and `home_header` in both English and French.

#### 4. Force Locale with URL Parameter

- Modify the `get_locale` function to check if a `locale` parameter is passed in the URL (e.g., `?locale=fr`).
- The app should use the locale from the URL if provided; otherwise, fall back to the default behavior.

#### 5. Mock User Login

- Implement a mock user login system with a predefined set of users. Each user has a name, locale, and timezone.
- Display a welcome message based on whether a user is logged in, and allow the user to log in via the `login_as` URL parameter.

#### 6. Use User Locale

- Modify the `get_locale` function to prioritize the user's preferred locale over other methods (URL parameter, request header, or default locale).

#### 7. Infer Appropriate Time Zone

- Create a `get_timezone` function to detect the user's time zone, first checking the URL parameter, then the user settings, and finally defaulting to UTC.
- Use `pytz` to validate the time zone.

#### 8. Display the Current Time (Advanced)

- Based on the inferred time zone, display the current time on the home page using the correct format.
- Provide translations for the time display in both English and French.

## Example Commands

- **Extract Messages for Translation:**
  ```bash
  pybabel extract -F babel.cfg -o messages.pot .
  ```

- **Initialize Translation Files:**
  ```bash
  pybabel init -i messages.pot -d translations -l en
  pybabel init -i messages.pot -d translations -l fr
  ```

- **Compile Translations:**
  ```bash
  pybabel compile -d translations
  ```

## Testing

- Ensure your app behaves as expected by visiting different URLs, such as:
  - `http://127.0.0.1:5000/` for the default locale.
  - `http://127.0.0.1:5000/?locale=fr` to test French translations.
  - `http://127.0.0.1:5000/?login_as=2` to simulate logging in as a user with a specific locale.

## Resources

- [Flask-Babel Documentation](https://flask-babel.tkte.ch/)
- [Flask i18n Tutorial](https://flask.palletsprojects.com/en/2.0.x/tutorial/i18n/)
- [pytz Documentation](https://pytz.sourceforge.io/)

## Requirements for Submission

- All files must end with a newline.
- Ensure all Python files are executable.
- Follow the project structure and naming conventions provided.
- The project must be completed on or before the deadline.

---