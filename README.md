```
def is_prime(num, n=2):
    if n >= num:
      return True
    if num % n == 0:
      return False
    return is_prime(num, n+1)


def primes(xs,i):
    if(len(xs)==i):
        return xs
    if (is_prime(xs[i]) == True):
        return primes(xs,i+1)
    else:
        xs.pop(i)
        return primes(xs,i)

L = [1,2,3,4,5,6,7,8,9]
print(primes(L,0))


def isDonee(a,b):
    if (a>=b):
        return True
    else :
        return False

def transformm(a,step):
    return a+step

def iterate(s, isDone, transform):
    if (isDone == False):
        print(s)
        return iterate(transform,isDonee(transform,20),transformm(transform,4))
    else:
        print("")


def rangeList(a, b, step):
    iterate(a,isDonee(a,b),transformm(a,step))


rList = rangeList(2, 20, 4)
print(rList) 



import queue
from threading import Thread
from queue import Queue
import random
import time

q = Queue(10)

class SenderThread(Thread):
    def run(self):
        global q
        nums = range(5)
        while True:
            num = random.choice(nums)
            q.put(num)
            print("Poslan", num)
            time.sleep(random.random())

class PortThread(Thread):
    def run(self):
        global q
        while True:
            data = q.get()
            q.task_done()
            print("Port primio", data)
            time.sleep(random.random())

SenderThread().start()
PortThread().start()
```
