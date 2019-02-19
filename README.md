# fitbit-test
Test gathering data from fitbit

# Installation

## Cloning
First, fork this repository (On the top right), so you can work on your own version independent of my changes. This essentially copies my repository and put it under your github as an independent copy.

Then, clone this repository to any directory you choose.

## Virtual Environment
It's always best to only include dependencies that you really need, the way to do this in Python is to use virtual environment. If you don't have it you can install [```virtualenv```](https://pypi.org/project/virtualenv/) by running the following in your commandline anywhere:
```
$ pip install virtualenv
```
After successful installation, go back to the root of your repository, and type the following
```
$ virtualenv venv
```
This creates a folder venv which has all your virtual environment files

I'm not exactly sure how on Mac this is done, but if you have Windows, you can do the following on Git Bash:
```
$ . venv/scripts/activate
```

If you're using PowerShell like me, you can just do:
```
$ venv/scripts/activate
```

This will activate your virtual environment, meaning any packages that you install are confined in the virtual environment.
The easiest way to tell if you're in a venv is if you see a ```(venv)``` at the beginning or above your commandline.

## Installing dependencies
Run the following code after you're inside a venv.
```
$ pip install -r requirements.txt
```
This will install all the dependencies inside the requirements.txt
I've pinned the versions of the package, so if they somehow get updated in the future you're going to be working with the version locked in this time.

## Specify your secrets
For security purpose, I've put your client secrets inside ```.gitignore```
So you have to create a secrets.py with the following fields:
```Python
CLIENT_ID = 'YOUR ID'
CLIENT_SECRET = 'YOUR TOKEN'
```

## Running your code
At this stage you should be set to simply run
```
$ python main.py
```
Which should eventually lead to the following error that you'd have to debug
```
500 Internal Server Error
The server encountered an unexpected condition which prevented it from fulfilling the request.

Traceback (most recent call last):
  File "C:\fitbit-test\venv\lib\site-packages\cherrypy\_cprequest.py", line 628, in respond
    self._do_respond(path_info)
  File "C:\fitbit-test\venv\lib\site-packages\cherrypy\_cprequest.py", line 687, in _do_respond
    response.body = self.handler()
  File "C:\fitbit-test\venv\lib\site-packages\cherrypy\lib\encoding.py", line 219, in __call__
    self.body = self.oldhandler(*args, **kwargs)
  File "C:\fitbit-test\venv\lib\site-packages\cherrypy\_cpdispatch.py", line 54, in __call__
    return self.callable(*self.args, **self.kwargs)
  File "C:\fitbit-test\gather_keys_oauth2.py", line 50, in index
    self.fitbit.client.fetch_access_token(code)
  File "C:\fitbit-test\venv\lib\site-packages\fitbit\api.py", line 146, in fetch_access_token
    code=code)
  File "C:\fitbit-test\venv\lib\site-packages\requests_oauthlib\oauth2_session.py", line 307, in fetch_token
    self._client.parse_request_body_response(r.text, scope=self.scope)
  File "C:\fitbit-test\venv\lib\site-packages\oauthlib\oauth2\rfc6749\clients\base.py", line 415, in parse_request_body_response
    self.token = parse_token_response(body, scope=scope)
  File "C:\fitbit-test\venv\lib\site-packages\oauthlib\oauth2\rfc6749\parameters.py", line 425, in parse_token_response
    validate_token_parameters(params)
  File "C:\fitbit-test\venv\lib\site-packages\oauthlib\oauth2\rfc6749\parameters.py", line 432, in validate_token_parameters
    raise_from_error(params.get('error'), params)
  File "C:\fitbit-test\venv\lib\site-packages\oauthlib\oauth2\rfc6749\errors.py", line 405, in raise_from_error
    raise cls(**kwargs)
oauthlib.oauth2.rfc6749.errors.InvalidClientError: (invalid_client)
```
