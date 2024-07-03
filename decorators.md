# Decorators &  First class functions & Closures


# Introduction

## First Class Function [youtube](https://www.youtube.com/watch?v=kr0mpwqttM0)
- Assign a function to a variable
```python
def square(x):
    return x*x

f= square(5)
print(f)
>>> 25

# Assign the function square to f
f= square 
print(f)
>>> function square at 0x...>

f(5)
>>>25


```
Note: f= square() means to **execute the function and place it into f**

- Passing a function as an argument to another function
The best example is the map() which take another function in the arguments.


```python
def my_map(func,arg_list):
    result = []
    for i in arg_list:
        result.append(func(i))
    return result


squares =my_map(square,[1,2,3,4,5]) # Note how we put square without parenthesis. So it is not executed
print(squares)
>>>[1,4,9,16,25]

```
- Return a function from another function (closure)

log_hi variable is at the end equal to log_message function. So we can run the log_hi variable as a function because it is a function doing log_hi() and execute it.

```python
def logger(msg):
    def log_message():
        print('Log:', msg)
    return log_message
log_hi=logger('Hi!')
log_hi()

>>> Log: Hi!
```





## Quick recap on Closures
[Closures](https://www.youtube.com/watch?v=swU3c34d2NQ)

```python
def out_funct():
    message='Hi'

    def in_funct():
        print(message)
    return in_funct()

my_func=out_funct()


my_func() #() are important!
>>> Hi
```


```python
def out_funct():
    message='Hi'

    def in_funct():
        print(message)
    return in_funct()

my_func=out_funct()


my_func() #() are important!
>>> Hi
```
         

```python
def out_funct():
    message='Hi'

    def in_funct():
        print(messsage)
    return in_funct # This means we return in_funct WITHOUT EXECUTING IT!!

my_funct=outer_function() #This means that in_funct is still waiting to be executed
my_funct() #Execution of the in_funct

>>> 
```


```python
def out_funct(msg):
    message=msg

    def in_funct():
        print(messsage)
    return in_funct # This means we return in_funct WITHOUT EXECUTING IT!!

hi_funct=out_funct('hi) #This means that in_funct is still waiting to be executed
bye_funct=out_funct('bye' #Execution of the in_funct

# Decorators

We have decorator function and wrapper function now.

```python
def decorator_fun(message):
    def wrapper_function():
        print(message)
    return wrapper_function
```

Now instead of a message as an argument of the decorator/outer_funct we will put a fonction called original function.
**BASICS OF DECORATORS**
```python
def decorator_fun(original_func):
    def wrapper_function():
        return original_funct()
    return wrapper_function

def display():
    print('display funt ran')


decorated_display= decorator_fun(display)
decorated_display()
>>> display funct ran
```

Decorating a function allows to add functionalities to our existing function  by additioning this functionaliy to the wrapper function.

```python
@decorator_fun
def display():
    print('...')

#This is the equivalent to
display= decorator_fun(display)
```
Note: You can use also class as decorators

# Property Decorator -> @property

```python
class Employee:
    def __init__(self,first,last):
        self.first = first
        self.last =last
        self.email =first + '.' +last + '@email.com'

    def fullname(self):
        return '{} {}'.format(self.first, self.last)

emp1=Employee('John', 'Smith')
emp1.first= 'Jim' # This will change the first name only but we are screwed for the email.

```
So we do the following

```python
class Employee:
    def __init__(self,first,last):
        self.first = first
        self.last =last
        self.email =first + '.' +last + '@email.com'
    @property # we can access email as an attributre even if it is a function
    def email(self):
        return '{}.{}@email.com'.format(self.first, self.last)

    def fullname(self):
        return '{} {}'.format(self.first, self.last)

emp1=Employee('John', 'Smith')
emp1.first= 'Jim' # This will change the first name only but we are screwed for the email.


print( emp1.first)
print(emp11.email)
print(emp1.fullname()) # Note here how fullname is not an attribute so we have to put ().
```


**Check @setter on youtube if needed**.




# Argument Decorator
Decorators that takes arguments.
Not very used. Maybe for flask and maybe fastapi?

```python
def decorator_function(original_function):
    def wrapper_function(*args, **kwargs):
        print('Executed Before',original_function.__NAME__)
        result = original_function(*args,**kwargs)
        print('Execuited After', original_function.__name__,'\n')
        return result
    return wrapper_function

@decorator_function
def display_info(name,age):
    print('display_info ran with arguments ({},{})'.format(name,age))


display_info('John',25)
display_info('Travis',30)

```

If we would like to add a custmosie prefix 

```python
def prefix_decorator(prefix):
    def decorator_function(original_function):
        def wrapper_function(*args, **kwargs):
            print('Executed Before',original_function.__NAME__)
            result = original_function(*args,**kwargs)
            print(prefix,'Execuited After', original_function.__name__,'\n')
            return result
        return wrapper_function
    return decorator_function

@prefix_decorator('LOG:')
def display_info(name,age):
    print('display_info ran with arguments ({},{})'.format(name,age))


display_info('John',25)
display_info('Travis',30)
