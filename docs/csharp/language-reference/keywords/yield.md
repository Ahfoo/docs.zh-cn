---
title: "yield（C# 参考） | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "yield"
  - "yield_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "yield 关键字 [C#]"
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 46
---
# yield（C# 参考）
如果你在语句中使用 `yield` 关键字，则意味着它在其中出现的方法、运算符或 `get` 访问器是迭代器。  通过使用 `yield` 定义迭代器，可在实现自定义集合类型的 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.IEnumerator> 模式时无需其他显式类（保留枚举状态的类，有关示例，请参阅 <xref:System.Collections.Generic.IEnumerator%601>）。  
  
 下面的示例演示了 `yield` 语句的两种形式。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## 备注  
 使用 `yield return` 语句可一次返回一个元素。  
  
 通过 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 语句或 LINQ 查询来使用迭代器方法。  `foreach` 循环的每次迭代都会调用迭代器方法。  迭代器方法运行到 `yield return` 语句时，会返回一个 `expression`，并保留当前在代码中的位置。  下次调用迭代器函数时，将从该位置重新开始执行。  
  
 可以使用 `yield break` 语句来终止迭代。  
  
 有关迭代器的详细信息，请参阅[迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 迭代器方法和 get 访问器  
 迭代器的声明必须满足以下要求：  
  
-   返回类型必须为 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
-   声明不能有任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 参数。  
  
 返回 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.IEnumerator> 的迭代器的 `yield` 类型为 `object`。如果迭代器返回 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.Generic.IEnumerator%601>，则必须将 `yield return` 语句中的表达式类型隐式转换为泛型类型参数。  
  
 你不能在具有以下特点的方法中包含 `yield return` 或 `yield break` 语句：  
  
-   匿名方法。  有关详细信息，请参阅[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。  
  
-   包含不安全的块的方法。  有关详细信息，请参阅[unsafe](../../../csharp/language-reference/keywords/unsafe.md)。  
  
## 异常处理  
 不能将 `yield return` 语句置于 try\-catch 块中。  可将 `yield return` 语句置于 try\-finally 语句的 try 块中。  
  
 可将 `yield break` 语句置于 try 块或 catch 块中，但不能将其置于 finally 块中。  
  
 如果 `foreach` 主体（在迭代器方法之外）引发异常，则将执行迭代器方法中的 `finally` 块。  
  
## 技术实现  
 以下代码从迭代器方法返回 `IEnumerable<string>`，然后遍历其元素。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 调用 `MyIteratorMethod` 并不执行该方法的主体。  相反，该调用会将 `IEnumerable<string>` 返回到 `elements` 变量中。  
  
 在 `foreach` 循环迭代时，将为 `elements` 调用 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法。  此调用将执行 `MyIteratorMethod` 的主体，直至到达下一个 `yield return` 语句。  `yield return` 语句返回的表达式不仅决定了循环体使用的 `element` 变量值，还决定了元素的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 属性（它是 `IEnumerable<string>`）。  
  
 在 `foreach` 循环的每个后续迭代中，迭代器主体的执行将从它暂停的位置继续，直至到达 `yield return` 语句后才会停止。  在到达迭代器方法的结尾或 `yield break` 语句时，`foreach` 循环便已完成。  
  
## 示例  
 下面的示例包含一个位于 `for` 循环内的 `yield return` 语句。  `Process` 中的 `foreach` 语句体的每次迭代都会创建对 `Power` 迭代器函数的调用。  对迭代器函数的每个调用将继续到 `yield return` 语句的下一次执行（在 `for` 循环的下一次迭代期间发生）。  
  
 迭代器方法的返回类型是 <xref:System.Collections.IEnumerable>（一种迭代器接口类型）。  当调用迭代器方法时，它将返回一个包含数字幂的可枚举对象。  
  
 [!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/csharp/yield_1.cs)]  
  
## 示例  
 下面的示例演示一个作为迭代器的 `get` 访问器。  在该示例中，每个 `yield return` 语句返回一个用户定义的类的实例。  
  
 [!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/csharp/yield_2.cs)]  
  
## C\# 语言规范  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 请参阅  
 [C\# 参考](../../../csharp/language-reference/index.md)   
 [C\# 编程指南](../../../csharp/programming-guide/index.md)   
 [foreach，in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)