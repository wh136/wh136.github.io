---
title: Python代码笔记
date: 2016-8-5 13:09:04
tags: [Python2.7]
---
### 记录入门Python2.7所写代码

```Python
#!/usr/bin/python 2.7
# -*- coding: utf-8 -*-

# print '------------------------------------------------------------------------------'
# print 'Hello,World!'
# print 1 + 2 + \
#     4 + 5
# print 'hello \nworld'
# print "\\nowhere"
#
# print '------------------------------------------------------------------------------'
# # Chapter2
# print '------------------------------------------------------------------------------'
# edward = ['Edward Sony', 42]
# john = ['John Smith', 50]
# database = [edward, john]
# print database
```
<!-- more -->
```Python
# greeting = 'hello'
# print greeting[0], '&', greeting[-1]
# number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# print number[3:6]
# print number[:3]
# print number[:]
# print(number[0:10:2])
# print(number[10:0:-2])
# print([1, 2, 3]+[4, 5, 6])
# print 'me'*10
# a = "Hello,World!"
# print('Hello' in a)
# print 'len =', len(number)
# print(max(number))
#
# # List method
# print list('Hello')
# x = [1, 1, 1]
# x[1] = 2
# print x
# name = ['Jack', 'Rose', 'Hua']
# del name[0]
# print name
# nameValueFor = ['P', 'e', 'r', 'l']
# print nameValueFor
# nameValueFor[2:] = list('ar')
# print nameValueFor
# nameValueFor[1:3] = []
# print nameValueFor
# nameValueFor.append('erl')
# print nameValueFor
# print nameValueFor.count('r')
# a = [1, 2, 3]
# b = [4, 5, 6]
# a.extend(b)
# print a
# a.insert(0, -1)
# print a
# print a.pop()
# print a
#
# a.remove(-1)
# print a
# a.reverse()
# print a
# a.sort()
# print a
# b = a.sort()
# print b
# print 1, 2, 3
# print ()
# print tuple([1, 2, 3])
# print tuple('abc')
# print tuple((1, 2, 3))
# # Chapter3
# print "hello,%s!" % 'world'
# from math import pi
# print "Pi=%.5f" % pi
# from string import Template
# s = Template('$x,glorious $x!')
# s.substitute(x='slam')
# print '%u + %u = %u' % (1, 1, 2)
# print '%10f' % pi
# print '%10.2f' % pi
# print '%.2f' % pi
# title = 'Hello,Python'
# print 'Dst =', title.find('Python')
# seq = ['1', '2', '3', '4', '5']
# plus = '+'
# print plus.join(seq)
# print "ABC".lower()
# print "1+2+3+4".split('+')
# print "/usr/bin/env".split('/')
# # Chapter4 dictionary
# phoneBook = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
# print phoneBook
# items = [('name', 'Gumby'), ('age', 42)]
# print dict(items)
# d = dict(items)
# print d['name']
# print dict(name='Nice', age=42)
# print "BasicMethodOfDictionary", "len =", len(phoneBook), "Alice's Phone = ", phoneBook['Alice']
# print "Gumby's phone number is %(Alice)s." % phoneBook
# # DeepCopy And shallowCopy
# from copy import deepcopy
# DeepCopyOfPB = deepcopy(phoneBook)
# phoneBook.clear()
# print "Phone = ", phoneBook
# print "DeepCopy = ", DeepCopyOfPB
# ShallowCopyOfPB = DeepCopyOfPB.copy()
# DeepCopyOfPB.clear()
# print "Shallow = ", ShallowCopyOfPB
# phoneBook = deepcopy(ShallowCopyOfPB)
# print "setdefault(key)", phoneBook.setdefault("Alice")

# # Chapter 5

# print 'age', 42
# import math as foobar
# print foobar.sqrt(4)
# x, y, z = 1, 2, 3
# print x, y, z
# x, y = y, x
# print x, y, z
# values = 1, 2, 3
# print values
# a, b, c = values
# print a
# # link valued
# from math import sqrt
# link1 = link2 = sqrt(4)
# print link1, link2
# print bool(42)
# name = raw_input("What's your name?")
# if name.endswith('Hua'):
#     print "Hello,Mr.Hua"
# else:
#     print "Hello,Stranger"
# num = raw_input("Enter a number.")
# if num > 0:
#     print "The number is positive"
# elif num < 0:
#     print "The number is negative"
# else:
#     print "The number is zero"
# assert
# age = 10
# assert 0 < age <100
# age = -1
# fishNum = 1
# assert 10 < fishNum < 100, 'Fish too less'
# x = 1
# while x <= 100:
#     print x
#     x += 1
# name = ''
# while not name:
#     name = raw_input("Please enter your name:")
#     print "Hello,%s" % name
# words = ['this', 'is', 'an', 'ex', 'parrot']
# for word in words:
#     print word
# d = {'x': 1, 'y': 2, 'z': 3}
# for key in d:
#     print key, 'correspond to', d[key]
# for key, value in d.items():
#     print key, 'correspond to', d[key]
# names = ['Anne', 'Beth', 'George', 'Damon']
# age = [12, 45, 32, 102]
# for i in range(len(names)):
#     print names[i], 'is', age[i], 'years old'
# from math import sqrt
# for n in range(99, 0, -1):
#     root = sqrt(n)
#     if root == int(root):
#         print n
#         break
# print [x*x for x in range(10) if x % 3 == 0]
# exec "print 'Hello,world'"
# from math import sqrt
# scope = {}
# exec 'sqrt=1' in scope
# print sqrt(4)
# print scope['sqrt']
# eval(raw_input("Enter a exp(Calculate):"))
# import math
# x = 1
# y = math.sqrt
# print callable(x)
# print callable(y)
#
#
# def hello(name):
#     return 'Hello,'+name+'!'
# print hello('World')
#
#
# def square(x):
#     """Calculate x*x"""
#     return x*x
# print square.__doc__
# print square(5)
#
#
# def test():
#     print 'This is print'
#     return
#     print 'This is not'
# print '----------------'
# x = test()
# print '----------------'
# print test()
# print '----------------'
# print x
#
#
# def try_to_change(n):
#     n = 'Mr.Hua'
# name = 'Jack'
# try_to_change(name)
# print name
#
#
# def change(n):
#     n[0] = "Mr.Tom"
# names = ['Mrs.Entity', 'Mr.Gates']
# change(names)
# print names
#
#
# storage = {}
# storage['first'] = {}
# storage['middle'] = {}
# storage['last'] = {}
# me = 'Magus lie het'
# storage['first']['Magus'] = [me]
# storage['middle']['lie'] = [me]
# storage['last']['het'] = [me]
# print storage['middle']['lie']
#
#
# # collection method
# def print_params(*params):
#     """single star return a tuple"""
#     print params
# print_params("Testing")
# print_params("Tsinghua", "university")
#
#
# def print_params_stars(**params):
#     """double star return a dictionary"""
#     print params
# print_params_stars(x=1, y=2, z=3)
#
#
# # reverse of collection
# def add(x, y):
#     return x+y
# params = (1, 2)
# print add(*params)
#
#
# def add_three(x, y, z):
#     return x+y+z
# params_tuple = {'x': 1, 'y': 2, 'z': 3, }
# print add_three(**params_tuple)
#
# # domain: variable is a dictionary vars() return a dictionary
# x = 1
# scope = vars()
# scope['x']
# scope['x'] += 1
# print x
#
# # global variable
# x = 1
#
#
# def change_global():
#     global x
#     x += 1
#
#
# def factorial(n):
#     if n == 1:
#         return 1
#     else:
#         return n*factorial(n-1)
# print factorial(10)
#
#
# def binary_search(sequence, number, lower, upper):
#     if lower == upper:
#         assert number == sequence[upper]
#         return upper
#     else:
#         middle = (lower + upper)//2
#         if number > sequence[middle]:
#             return binary_search(sequence, number, middle + 1, upper)
#         else:
#             return binary_search(sequence, number, lower, middle)
#
# seq = [50, 21, 32, 22, 94, 80, 1, 6]
# seq.sort()
# print seq
# print "The dst of Number is", binary_search(seq, 22, 0, len(seq)-1) + 1
# L = []
# n = 1
# while n <= 99:
#     L.append(n)
#     n += 2
# print L
# higher-order function:function and variable
# x = abs(-10)
# print x
# print abs
# f = abs
# y = f(-10)
# print y
#
#
# def add(a, b, function):
#     return function(a)+function(b)
# print "This function program result is:", add(-10, -10, f)
# built in function:map and reduce
#
#
# def f(x):
#     return x*x
# print map(f, [1, 2, 3, 4, 5])
#
# print map(str, [1, 2, 3, 4, 5])
#
# reduce function receive two params x1,x2.Input f get y1,then input f with y1 and x3,and so on
#
#
# def fn(x, y):
#     return x*10+y
# reduce(fn, [1, 3, 5, 7, 9])
#
#
# def char2num(s):
#     return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]
#
# print reduce(fn, map(char2num, '13579'))
# print map(char2num, '123456')
#
#
# def str2int(s):
#     def fn(x, y):
#         return x*10+y
#     def char2num(str_num):
#         return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[str_num]
#     return reduce(fn, map(char2num, s))
#
#
# def str2int_lambda(s):
#     return reduce(lambda x, y: x*10+y, map(char2num, s))
# transfer the username into regular (nAMe into Name)using map
# User = ['adam', 'LISA', 'barT']
#
#
# def user_reg(user_list):
#         return user_list.title()
#
#
# def regular_name(name):
#     return map(user_reg, name)
# print regular_name(User)
# # using lambda below
#
#
# def regular_name_lambda(name):
#     return map(lambda x: x.title(), name)
# print regular_name(User)
#
# # List multiply
# a = [50, 32, 7, 12, 56, 18]
#
#
# def multiply_list_lambda(list_num):
#     return reduce(lambda x, y: x*y, list_num)
# print multiply_list_lambda(a)
#
# # filter-sequence find odd num del rest
#
#
# def is_odd(n):
#     return n % 2 == 1
# print filter(is_odd, a)
#
# sequence = ['A', '', None, '  ']
#
#
# def not_empty(s):
#     return s and s.strip()
# print filter(not_empty, sequence)

# find all prime number in 0-99 and print the calculate times
#
# from math import sqrt
#
# list_1 = []
# list_2 = []
# list_3 = []
#
#
# def is_prime(number):
#     flag = True
#     time = 0
#     global list_1
#     if number == 2:
#         return flag
#     elif number < 2:
#         return False
#     for i in range(2, number):
#         if number % i == 0:
#             flag = False
#             time += 1
#             break
#         else:
#             time += 1
#     list_1.append(time)
#     return flag
#
#
# def is_prime_second(number):
#     flag = True
#     time = 0
#     global list_2
#     if number == 2:
#
#         return flag
#     elif number < 2:
#         return False
#     for i in range(2, number/2):
#         if number % i == 0:
#             flag = False
#             time += 1
#             break
#         else:
#             pass
#     list_2.append(time)
#     return flag
#
#
# def is_prime_three(number):
#     flag = True
#     time = 0
#     if number == 2:
#         return flag
#     elif number < 2:
#         return False
#     for i in range(2, int(sqrt(number))):
#         if number % i == 0:
#             flag = False
#             time += 1
#             break
#         else:
#             pass
#     list_3.append(time)
#     return flag
#
#
# def add(x, y):
#     return x + y
#
#
# for i in range(0, 99):
#     is_prime(i)
#
#
# for i in range(0, 99):
#     is_prime_second(i)
#
#
# for i in range(0, 99):
#     is_prime_three(i)
#
# print "The prime of sequence is:", filter(is_prime, range(0, 99))
# print "Method one cal times:", reduce(add, list_1)
# print "The prime of sequence is:", filter(is_prime_second, range(0, 99))
# print "Method two cal times:", reduce(add, list_2)
# print "The prime of sequence is:", filter(is_prime_three, range(0, 99))
# print "Method three cal times:", reduce(add, list_3)

# chapter 6
# function as a value return :closure program
#
#
# def lazy_sum(*args):
#     def sum_test():
#         ax = 0
#         for n in args:
#             ax += n
#         return ax
#     return sum_test
#
# f = lazy_sum(1, 3, 5, 7)
# print f()

#
# def count():
#     fs = []
#     for i in range(1, 4):
#         def f():
#             return i*i
#         fs.append(f)
#     return fs
#
#
# f1, f2, f3 = count()
# print f1()
# print f2()
# print f3()

# lambda function unnamed
# calculate f(x)=x^2
# print map(lambda x: x*x, [1, 2, 3, 4])
#
#
# def f(x):
#     return x*x
#
# print map(f, [1, 2, 3, 4])
#
# # decorator
#
#
# def now():
#     print'2016-9-1'
#
# g = now
# print g()
# print 'now function name:', now.__name__, 'g function name:', g.__name__
#
# # example 1
#
#
# def log_decorator(func):  # decorator
#     def wrapper(*args, **kw):
#         print 'call %s():' % func.__name__
#         return func(*args, **kw)
#     return wrapper
#
#
# @log_decorator
# def now_next():
#
#     print '2016-10-1'
#
# now_next()
#
# # example 2

#
# def log_decorator(text):
#     def decorator(func):
#         def wrapper(*args, **kw):
#             print '%s %s():' % (text, func.__name__)
#             return func(*args, **kw)
#         return wrapper
#     print 'run decorator'
#     return decorator
#
#
# @log_decorator('execute')
# def now():
#     print '2016-10-1'
#
# now()
# run sequence:log_decorator()-wrapper()- return func()[now()]- now()-return wrapper- decorator()-return decorator






# produce and consumer multi threading
# multi processing Unix/Linux fork()
#
# import os
# # window didn't include fork()
# print 'Process (%s) start.' % os.getpid()
#
# pid = os.fork()
#
# if pid == 0:
#     print "I am child process (%s) and my parent is %s.", (os.getpid(), os.getppid())
# else:
#     print "I am (%s) just created a child process (%s)." % (os.getppid(), pid)
#
# from multiprocessing import Process
# import os
#
# # child process run
#
#
# def child_run(name):
#     print 'Run child process %s (%s)...' % (name, os.getpid())
# if __name__ == '__main__':
# print 'Parent process %s ' % os.getpid()
# p = Process(target=child_run, args=('test',))
# print "Process will start."
# p.start()
# p.join()
# print 'Process kill'
#
#
#
# from multiprocessing import Process, Queue
# import os, time, random
#
#
#
# def write(q):
#     for value in ['A', 'B', 'C', 'D', 'E']:
#         print "Put %s to queue" % value
#         q.put(value)
#         time.sleep(random.random())
#
#
# def read(q):
#     while True:
#         value = q.get(True)
#         print "Get %s from queue." % value
#
# if __name__ == '__main__':
#     q = Queue()
#     pw = Process(target=write, args=(q,))
#     pr = Process(target=read, args=(q,))
# # reading and writing
#     pw .start()
#     pr.start()
# # waiting pw end. A, B, C, D, E write finished
#     pw.join()
# # pr is endless a loop,must be terminate
#     pr.terminate()
#
# # threading thread POSIX
# import time,threading
# # new thread execute
#
#
# def loop():
#     print 'thread %s is running...' % threading.current_thread().name
#     n = 0
#     while n < 5:
#         n += 1
#         print 'thread %s >>> %s' % (threading.current_thread().name, n)
#         time.sleep(1)
#     print 'thread %s ended.' % threading.current_thread().name
#
# print 'thread %s is running...' % threading.current_thread().name
# # built thread object using Thread
# t = threading.Thread(target=loop, name='LoopThread')
# t.start()
# t.join()
# print 'thread %s ended.' % threading.current_thread().name

# Lock:Process copy variable,Thread share one variable
# example how Thread change one variable
#
# import time, threading
# # this in my bank savings
# balance = 0
#
#
# def change_it(n):
#     global balance
#
#     balance += n
#     balance -= n
#
#
# def run_thread(n):
#     for i in range(100000):
#         change_it(n)
#
# t1 = threading.Thread(target=run_thread, args=(5,))
# t2 = threading.Thread(target=run_thread, args=(8,))
#
# t1.start()
# t2.start()
# t1.join()
# t2.join()
# print balance
# import threading, Queue, time
#
#
# class Consumer(threading.Thread):
#     def __init__(self, queue):
#         threading.Thread.__init__(self)
#         self.__queue = queue
#
#     def run(self):
#         while True:
#             msg = self.__queue.get()
#             if isinstance(msg, str) and msg == 'quit':
#                 break
#             print "I am thread, and i received %s" % msg
#         print 'bye'
#
#
# def Producer():
#     queue = Queue.Queue()
#     worker = Consumer(queue)
#     worker.start()
#     start_time = time.time()
#     while time.time()-start_time < 5:
#         queue.put('something at %s' % time.time())
#         time.sleep(1)
#     queue.put('quit')
#     worker.join()
#
# if __name__ == '__main__':
#     Producer()
#
# import threading, zipfile
#
# class AsyncZip(threading.Thread):
#     def __init__(self, infile, outfile):
#         threading.Thread.__init__(self)
#         self.infile = infile
#         self.outfile = outfile
#     def run(self):
#         f = zipfile.ZipFile(self.outfile, 'w', zipfile.ZIP_DEFLATED)
#         f.write(self.infile)
#         f.close()
#         print 'Finished background zip of: ', self.infile
#
# background = AsyncZip('mydata.txt', 'myarchive.zip')
# background.start()
# print 'The main program continues to run in foreground.'
#
# background.join()    # Wait for the background task to finish
# print 'Main program waited until background was done.'
#

#
#
# def TrimFuc(strs):
#
#     head=0
#     tail=len(strs)
#     while(head<tail and (strs[head].isspace() or strs[head]=="\x00")):
#            head += 1
#     if head == tail:
#            return ""
#     while(strs[tail-1].isspace() or strs[tail-1]=="\x00"):
#            tail -= 1
#     return strs[head:tail]
#
# strs = ' hello,world\n'
# strs1 = 'hello,world\n'
# print strs
# print '-----------------'
# print TrimFuc(strs)
# print TrimFuc(strs1)
# print '-----------------'
#
# # regular expression
#
# import re
# # match success will return a object of match else return None
# print re.match(r'^\d{3}\-\d{3,8}$', '010-12345')
# print re.match(r'^\d{3}\-\d{3,8}$', '010 12345')
# print '-----------------------------------------'
# # split string with reExp and common
# print re.split(r'\s+', 'a b   c')
# print 'ab    c'.split()
# print re.split(r'[\s\,]+', 'a,b, c  d')
# print re.split(r'[\s\,\;]+', 'a,b;;  c  d')
# # group substring
# m = re.match(r'^(\d{3})-(\d{3,8})$', '010-12345')
# print m
# print m.group(0)
# print m.group(1)
# print m.group(2)
#
# print re.match(r'^(\d+)(0*)$', '102300').groups()
# print re.match(r'^(\d+?)(0*)$', '102300').groups()
#
# re_telephone = re.compile(r'^(\d{3})-(\d{3,8})$')
# print re_telephone.match('010-8086').groups()
#
# print'--------------------------------------'
# print re.match(r'[a-z]', 'a44')
#

# json
# import json
# obj = [[1, 2, 3], 1992, 6.12, 'Sam', {'key': (4, 5, 6), 'Tom': (7, 8, 9)}]
# encode_json = json.dumps(obj)
# print repr(obj)
# print encode_json
# print 'encode_json_type', type(encode_json)
# decode_json = json.loads(encode_json)
# print 'decode_json_type', type(decode_json)
# print decode_json[4]['key']
# print decode_json
# import re
#
# fields = "oracle_username=xiaweihua"
# print re.sub('oracle_username=', '', fields)


# file_t = open('hello.data', 'w')
# for line in range(0, 9):
#     file_t.write(str(line)+'\n')
# file_t.close()
#
# file_r = open('hello.data', 'r')
# print '--------'
# for line in range(0, 9):
#     print file_r.readline()
#     print '---------'
#
# file_r.close()
# conn = cx_Oracle.connect('themis', 'themis', '192.168.1.60/testdb')
# dsn_tns = cx_Oracle.makedsn('themis', 'themis', '192.168.1.60/testdb')
# c = conn.cursor()
# data = c.execute('desc t_redlist')
# print  data.fetchall()

# encoding decoding formal
# tup = ('abc', '123', '\xce\xf7\xb0\xb2')
# print tup[2].decode('gbk')
#
# from random import randint
# from time import sleep, ctime
# from Queue import Queue
# import threading
#
#
# class MyThread(threading.Thread):
#     def __init__(self, func, args, name=''):
#         threading.Thread.__init__(self)
#         self.name = name
#         self.func = func
#         self.args = args
#
#     def get_result(self):
#         return self.res
#
#     def run(self):
#         print 'starting', self.name, 'at', ctime()
#         self.res = self.func(*self.args)
#         print self.name, 'finished at:', ctime()
#
#
# def write_queue(queue):
#     print 'produce apple for queue...'
#     queue.put('apple', 1)
#     print 'apple number now is:', queue.qsize()
#
#
# def read_queue(queue):
#     val = queue.get(1)
#     print 'consume a %s from queue...' % val
#     print 'apple number now is:', queue.qsize()
#
#
# def writer(queue, loops):
#     for i in range(loops):
#         write_queue(queue)
#         sleep(randint(1, 3))
#
#
# def reader(queue, loops):
#     for i in range(loops):
#         read_queue(queue)
#         sleep(randint(2, 5))
#
#
# funcs = [writer, reader]
# nfuncs = range(len(funcs))
#
#
# def main():
#     nloops = randint(2, 5)
#     q = Queue(32)
#
#     threads = []
#     for i in nfuncs:
#         t = MyThread(funcs[i], (q, nloops), funcs[i].__name__)
#         threads.append(t)
#
#     for i in nfuncs:
#         threads[i].start()
#
#     for i in nfuncs:
#         threads[i].join()
#
#     print 'all done'
#
# if __name__ == '__main__':
#     main()

# transform dictionary to XML
from xml.etree.ElementTree import Element, SubElement, tostring
from xml.dom.minidom import parseString

# BOOKs = {
#     '013269937': {
#         'title': 'Core Python Programming',
#         'edition': 2,
#         'year': 2006,
#     },
#     '0132356139': {
#         'title': 'Python web development with Django',
#         'authors': 'Jeff Forcier:Paul Bissex:Wesley Chun',
#         'year': 2009,
#     },
#     '0137143419': {
#         'title': 'Python Fundamentals',
#         'year': 2009,
#     },
# }
# books = Element('books')
# for isbn, info in BOOKs.iteritems():
#     book = SubElement(books, 'book')
#     info.setdefault('authors', 'Wesley Chun')
#     info.setdefault('edition', 1)
#     for key, val in info.iteritems():
#         SubElement(book, key).text = ', '.join(str(val).split(':'))
#
# xml = tostring(books)
# print '****Raw XML****'
# print xml
#
# print '\n***Pretty Printed XML'
# dom = parseString(xml)
# print dom.toprettyxml('    ')
#
#
# print '***Flat Structure***'
# for elmt in books.iter():
#     print elmt.tag, '-', elmt.text
#
# print '\n****Titles Only****'
# for book in books.findall('.//title'):
#     print book.text


pointfile = open('test.txt', 'w')
pointfile.write('Hello, world')
pointfile.close()

file_read = open('test.txt', 'r')
print file_read.read(4)
print file_read.read()

write_again = open('test.txt', 'w')
write_again.write('write again.')
write_again.close()


```



版权声明：本文为博主制作文章，转载时注明，谢谢。
