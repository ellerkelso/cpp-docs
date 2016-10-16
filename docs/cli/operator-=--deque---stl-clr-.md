---
title: "operator&gt;= (deque) (STL-CLR)"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator>= member [STL/CLR]"
ms.assetid: 14746073-60a3-4088-b7ea-f987e963d418
caps.latest.revision: 15
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# operator&gt;= (deque) (STL/CLR)
Deque greater than or equal comparison.  
  
## Syntax  
  
```  
template<typename Value>  
    bool operator>=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### Parameters  
 left  
 Left container to compare.  
  
 right  
 Right container to compare.  
  
## Remarks  
 The operator function returns `!(``left` `<` `right``)`. You use it to test whether `left` is not ordered before `right` when the two deques are compared element by element.  
  
## Example  
  
```  
// cliext_deque_operator_ge.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**[a b c] >= [a b c] is True**  
**[a b c] >= [a b d] is False**   
## Requirements  
 **Header:** \<cliext/deque>  
  
 **Namespace:** cliext  
  
## See Also  
 [deque (STL/CLR)](../cli/deque--stl-clr-.md)   
 [operator== (deque) (STL/CLR)](../cli/operator==--deque---stl-clr-.md)   
 [deque::operator!= (STL/CLR)](../cli/deque--operator!=--stl-clr-.md)   
 [operator\< (deque) (STL/CLR)](../cli/operator---deque---stl-clr-.md)   
 [operator> (deque) (STL/CLR)](../cli/operator---deque---stl-clr-.md)   
 [operator<= (deque) (STL/CLR)](../cli/operator-=--deque---stl-clr-.md)