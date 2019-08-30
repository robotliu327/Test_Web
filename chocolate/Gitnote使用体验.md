# gitnote使用体验
1. 图片
	![嘻嘻](0)
2. 代码的使用
首先来讲一个很经典的问题，就是出栈顺序，题目是这样的，比如现在又1 2 3 4 5五个数字，规定这五个数字入栈的顺序不变，但是中间可以任意的出栈，出栈的数字就当做输出，请写出程序输出所有的出栈的序列
这个问题可以用很经典的回溯法来解，就是通过递归方法调用，在每一层找出所有可能的操作方式，直到全部输出，另外需要加一句的是在以前我是不知道递归的时候还原现场的，在这个代码里面也是学到了这个知识点，而这个小细节其实是很重要的，当时就是因为这个细节让我在思考递归调用的时候否定了该方法，后来想了许久才重新相通
```JAVA
public static void SearchStack(Stack<int> input, Stack<int> stack, Stack<int> output)
{
    if (input.Count == 0 && stack.Count == 0)
    {
        //输出结果
        Array array = output.ToArray();
        foreach (int obj in array)
            Console.Write(obj);
        Console.WriteLine("");

    }
    else
    {
        if (input.Count > 0)
        {
            //入栈
              stack.Push(input.Pop());
            SearchStack(input, stack, output);
            input.Push(stack.Pop());
        }

        if (stack.Count > 0)
        {
            //出栈
              output.Push(stack.Pop());
            SearchStack(input, stack, output);
            stack.Push(output.Pop());
        }
    }
}

```

