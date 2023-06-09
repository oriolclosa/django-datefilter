# Django admin date filter

[![GitHub release](https://img.shields.io/github/release/oriolclosa/django-daterangefilter.svg)](https://github.com/oriolclosa/django-daterangefilter/releases/latest)
[![GitHub issues](https://img.shields.io/github/issues/andreynovikov/django-daterangefilter.svg)](https://github.com/oriolclosa/django-daterangefilter/issues)
[![GitHub license](https://img.shields.io/github/license/andreynovikov/django-daterangefilter.svg)](LICENSE)

Based on Andrey Novikov's `django-daterangefilter`.

## Requirements

* Python 3.7+
* Django 3.6, 4.1 or 4.2

## Installation

Add ```daterangefilter``` to ```INSTALLED_APPS```. Example:

```python
INSTALLED_APPS = (
    ...
    'daterangefilter',
    ...
)
```

Application uses static files so do not forget to issue ```collectstatic``` management command in production environment.

## Example usage

in admin.py:

```python
from django.contrib import admin
from daterangefilter.filters import PastDateRangeFilter, FutureDateRangeFilter

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
    list_filter = [
        ('created_at', PastDateRangeFilter), ('publish_at', FutureDateRangeFilter)
    ]
```

## Advanced usage

Predefined ranges can be completely redefined by overriding ```_past_ranges.html``` and ```_future_ranges.html``` templates.
Take into account that these templates are inserted in the middle of the javascript code and may contain nothing but ranges
definition. For more examples on using ```moment``` library refer to [library documentation](https://momentjs.com/docs/#/manipulating/).

## Credits

Filter widget uses a great JavaScript date range picker component - [Date Range Picker](https://github.com/dangrossman/daterangepicker) by Dan Grossman.
