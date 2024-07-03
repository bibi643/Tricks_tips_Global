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
def out_funct(msg):
    message=msg

    def in_funct():
        print(messsage)
    return in_funct()

hi_func=out_funct('hi')
bye_funct= out_func('bye')


hi_func()
bye_funct()
>>> Hi
>>>Bye
>>> 
```


# Property Decorator


# Argument Decorator
