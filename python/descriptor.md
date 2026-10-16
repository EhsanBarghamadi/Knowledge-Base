---
title: Descriptor در Python
tags: [python, descriptor, data-model]
reviewed: 2026-10-16
---

## خلاصه
به طور کلی Descriptor در پایتون آبجکت‌هایی هستن که به ما این اجازه رو می‌دن روی سه عملیات **class attribute‌** کنترل داشته باشیم:

1. خواندن و دسترسی به مقدار attribute
2. ست کردن مقدار برای یک attribute
3. حذف کردن یک attribute

## شرح مفهوم
سینتکس پیاده‌سازی:

```python
class MyDescriptor:
    def __get__(self, obj, objtype=None):
        ...

    def __set__(self, obj, value):
        ...

    def __delete__(self, obj):
        ...


class MyClass:
    class_attribute = MyDescriptor()
```

همون‌طور که از روی اسم‌ها مشخصه، `__get__` برای پیاده‌سازی منطق خواندن مقدار، `__set__` برای منطق ست کردن مقدار و `__delete__` برای منطق حذف کردن یک attribute استفاده می‌شه.

بر اساس اینکه یک Descriptor چه منطق‌هایی رو پیاده‌سازی کرده، به دو نوع تقسیم می‌شه:

1. **Data Descriptor:** باید حداقل `__set__` یا `__delete__` برای اون تعریف شده باشه.
2. **Non-Data Descriptor:** فقط `__get__` براش تعریف شده.

## منبع
- [مستندات پایتون](https://docs.python.org/3/howto/descriptor.html)