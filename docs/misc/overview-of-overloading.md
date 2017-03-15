---
title: "Vue d&#39;ensemble de la surcharge | Microsoft Docs"
ms.custom: ""
ms.date: "11/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fonction de surcharge, à propos de la surcharge de fonction"
  - "surcharge d’opérateur, à propos de la surcharge d’opérateur"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Vue d&#39;ensemble de la surcharge
Avec le langage C\+\+, vous pouvez surcharger des fonctions et des opérateurs. La surcharge consiste à fournir plusieurs définitions pour un nom de fonction donné se trouvant dans la même portée. Le compilateur est autorisé à choisir la version appropriée de la fonction ou l'opérateur selon les arguments avec lesquels il est appelé. Par exemple, la fonction max est considérée comme une fonction surchargée. Elle peut être utilisée dans le code comme suit :  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 Dans le premier appel de fonction, où la valeur maximale de deux variables de type `int` est demandée, la fonction `max( int, int )` est appelée. En revanche, dans le second appel de fonction, les arguments sont de type `double`, par conséquent c'est la fonction `max( double, double )` qui est appelée.  
  
## Voir aussi  
 [Surcharge \(C\+\+\)](../misc/overloading-cpp.md)