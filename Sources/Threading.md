# Threading
Every Program having one Main Thread under process

Procces <br/>
-- Threading <br/>
   --- Singal Threading<br/>
   --- Multithreading 

<br/>
<br/>


Singal/Main Thread <br/>
```
using System;

class SingalThreadDemo{
void main(){
}

}

```

MultiThreading <br/>
```
using System;
using System.Threading;

 class Program
    {
        static void Main()
        {
            Thread T1 = new Thread(Method_1);
            Thread T2 = new Thread(Method_2);
            Thread T3 = new Thread(Method_3);
            T1.Start();
            T2.Start();
            T3.Start();
            Console.ReadLine();
        }
        static void Method_1()
        { // Method 1
            for (int i = 0; i<= 15; i++)
            {
                Console.WriteLine("Line: " + i + " M 1");
                if (i == 5)
                {
                    Console.WriteLine("Line: " + i + " M 1 Stopped");
                    Thread.Sleep(5000);
                    Console.WriteLine("Line: " + i + " M 1 Started");
                }
            }
        }
        static void Method_2()
        { // Method 2
            for (int i = 0; i <= 15; i++)
            {
                Console.WriteLine("Line: " + i + " M 2");
            }
        }
        static void Method_3()
        { // Method 3
            for (int i = 0; i <= 15; i++)
            {
                Console.WriteLine("Line: " + i + " M 3");
            }
        }
    }
```

## Constructor 
we will always need to match the signature(type) of a method to the signature(type) of same kind of deligate. that why we need this 4 kinds of Constructor
It's a deligate <br/>

1 - Thread T1 = new Thread(ThreadStart obj)  // for Void and non-parameterized : the passing function should be void return type and non-parameterized <br/> 
2-  Thread T1 = new Thread(ParameterizedThreadStart obj)  <br/>
1 - Thread T1 = new Thread(ParameterizedThreadStart obj, Int maxStackSize) <br/>
1 - Thread T1 = new Thread(ThreadStart obj, Int maxStackSize)  <br/>

## Concept
### 1 - Thread T1 = new Thread(ThreadStart obj) <br/>

why we use? what is diffrent between this one and without this? as we se multithread without this:
for explicitly programmer if we will not, then framework or CLR responsiable for use this implicitly.
Note : there is no any effect we will use ot Not


To use threading we need to matching signature(type) method type == deligate type 
1 We need to define a deligate. but That is already Define by System.Threading NameSpace <br/>
``` public delegate void ThreadStart Ts1 = new ShreadStart(Method_1); // definde explicitly(); ```
 
2 instance setting a deligate. It is a process to binding a method with the delegagte. // 
so here we need to binding the method that which one we want to bind with the deligate
``` 
Thread T1 = new Thread(Method_1); // now pass that method as a deligate, this is called implicitly bind
T1.Start():
```
OR 
```
ThreadStart Ts1 = new ShreadStart(Method_1); // bind the method with the same type of deligate
Thread T1 = new Thread(Ts1); // now pass that deligate
T1.Start():
``` 
both codes working as same 

<details><summary>CLICK ME</summary>
```
using System;
using System.Threading;
 class Program
    {
        static void Main()
        {
            ThreadStart Ts1 = new ThreadStart(Method_1);
            Thread T1 = new Thread(Ts1);
            T1.Start();  
            Thread T2 = new Thread(Method_2);
            Thread T3 = new Thread(Method_3);
            T1.Start();
            T2.Start();
            T3.Start();
            Console.ReadLine();
        }
        static void Method_1()
        { // Method 1
            for (int i = 0; i<= 15; i++)
            {
                Console.WriteLine("Line: " + i + " M 1");
                if (i == 5)
                {
                    Console.WriteLine("Line: " + i + " M 1 Stopped");
                    Thread.Sleep(5000);
                    Console.WriteLine("Line: " + i + " M 1 Started");
                }
            }
        }
        static void Method_2()
        { // Method 2
            for (int i = 0; i <= 15; i++)
            {
                Console.WriteLine("Line: " + i + " M 2");
            }
        }
        static void Method_3()
        { // Method 3
            for (int i = 0; i <= 15; i++)
            {
                Console.WriteLine("Line: " + i + " M 3");
            }
        }
    }
```
