---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a>/optionexplicit
如果在使用之前，不声明变量，会导致编译器报告错误。  
  
## <a name="syntax"></a>语法  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>参数  
 `+` &#124; `-`  
 可选。 指定`/optionexplicit+`若要要求显式声明变量。 `/optionexplicit+`选项是默认设置，并为相同`/optionexplicit`。 `/optionexplicit-`选项，可以隐式声明变量。  
  
## <a name="remarks"></a>备注  
 如果源代码文件包含[Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，语句将覆盖`/optionexplicit`命令行编译器设置。  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中设置 /optionexplicit  
  
1.  在 “解决方案资源管理器”中选择一个项目。 在“项目”菜单上，单击“属性”。 有关详细信息，请参阅[项目设计器简介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  单击“编译”选项卡。  
  
3.  修改中的值**Option Explicit**框。  
  
## <a name="example"></a>示例  
 下面的代码编译时`/optionexplicit-`使用。  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [“选项”对话框 ->“项目”->“Visual Basic 默认值”](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
