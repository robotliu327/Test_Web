# gitnote使用体验
1. 图片
	![嘻嘻](0)
2. 代码的使用
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
