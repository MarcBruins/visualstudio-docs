---
title: "&#39;Loop&#39; cannot have a condition if matching &#39;Do&#39; has one"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
manager: douge
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# &#39;Loop&#39; cannot have a condition if matching &#39;Do&#39; has one
A `Loop` statement contains a `While` or `Until` clause, and the corresponding `Do` statement also contains such a clause. Only one of the `Do` and `Loop` statements in a loop can specify a condition.  
  
 **Error ID:** BC30238  
  
### To correct this error  
  
-   Remove the `While` or `Until` clause from either the `Do` statement or the `Loop` statement.  
  
## See Also  
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)