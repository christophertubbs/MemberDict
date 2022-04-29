# MemberDict
A dictionary data type that grants access to value via attribute access as well as subscript access

# Example

```python
>>> member_dict = memberdict()
>>> member_dict.__dict__
{}
>>> member_dict['example'] = value
>>> member_dict['example']
'value'
>>> member_dict.example
'value'
>>> x.__dict__
{'example': 'value'}
```

# Use Case

Consider the following:

```python
>>> import requests

>>> with requests.get("https://example.com/rest/endpoint/arg") as response:
>>>     response_data = response.json()
>>> print(response_data)
```

and you get:

```json
{
    "name": "Example Response",
    "values": [
        {
            "descriptor": "The first item in the response values",
            "data": [
                1, 2, 3, 4, 5
            ]
        },
        {
          "descriptor": "The second item in the response values",
          "data": [
              6, 7, 8, 9
          ]
        }
    ]
}
```

You can use:

```python
>>> response_dict = memberdict(response_data)
>>> response_dict['name']
'Example Response'
>>> response_dict.name
'Example Response'
>>> print(response_dict.values[0].descriptor)
'The first item in the response values'
```

The memberdict will be recursive, so adding dictionaries to the member dictionary will make its children _also_ memberdicts.

# Nice to Have

- [ ] Query by xpath
- [ ] XML Etree conversion
