# simple-python-rest-api-v1
Simple python REST API with docker and travis-ci 


[![Build Status](https://travis-ci.org/jkogut/simple-python-rest-api-v1.svg?branch=master)](https://travis-ci.org/jkogut/simple-python-rest-api-v1)
[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)

Install
-------

Clone the repo first and then build the docker image and run it:

```
git clone git@github.com:jkogut/simple-python-rest-api-v1.git

docker build --tag simple_python_rest_api .

docker run -p 127.0.0.1:5002:5002 -d simple_python_rest_api
```

Run tests with *pytest*:

```
py.test -v -l test_rest_api_docker.py
```


Test
----

Test available endpoints with *curl*:

 * [GET] API status *http://0.0.0.0:5002/api/status*
 * [GET] Employees  *http://0.0.0.0:5002/api/v1/employees*
 * [GET] Employee full data   *http://0.0.0.0:5002/api/v1/employees/EmployeeId*
 * [POST] Create new employee *http://0.0.0.0:5002/api/v1/employees/new*
 * [DELETE] Delete employee *http://0.0.0.0:5002/api/v1/employees/delete/EmployeeId*
 
Example usage: 
```
curl http://0.0.0.0:5002/api/status |jq
curl http://0.0.0.0:5002/api/v1/employees |jq
curl http://0.0.0.0:5002/api/v1/employees/1 |jq
curl -H "Content-Type: application/json" -X POST -d@payload.json http://0.0.0.0:5002/api/v1/employees/new |jq
curl -X DELETE http://0.0.0.0:5002/api/v1/employees/delete/9 |jq
```

Debug
-----

Clone the repo:

```
git clone git@github.com:jkogut/simple-python-rest-api-v1.git
```

Use `virtualenv` and install dependencies with `pip`:
```
virtualenv venv
source venv/bin/activate
pip install -r app/requirements.txt
```

Run flask rest application in `debug mode`:
```
cd app;
python rest_server.py
```
