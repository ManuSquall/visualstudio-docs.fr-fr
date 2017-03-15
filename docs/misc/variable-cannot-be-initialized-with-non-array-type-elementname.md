---
title: "La variable ne peut pas &#234;tre initialis&#233;e avec un type autre qu’un type tableau &#39;&lt;nom_&#233;l&#233;ment&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable ne peut pas &#234;tre initialis&#233;e avec un type autre qu’un type tableau &#39;&lt;nom_&#233;l&#233;ment&gt;&#39;
Une variable déclarée en tant que tableau doit être initialisée avec une valeur de tableau.  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **ID d’erreur :** BC36536  
  
### Pour corriger cette erreur  
  
-   Initialisez la variable de tableau avec une valeur de tableau :  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## Voir aussi  
 [NOTINBUILD Variable tableau](http://msdn.microsoft.com/fr-fr/c2da78bd-6928-46ba-805f-44f819dfaf93)