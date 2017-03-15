---
title: "Impossible de d&#233;duire un type de donn&#233;es pour &#39;&lt;nom_variable&#39;, car les dimensions du tableau ne correspondent pas | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire un type de donn&#233;es pour &#39;&lt;nom_variable&#39;, car les dimensions du tableau ne correspondent pas
Si les dimensions utilisées pour initialiser un tableau ne correspondent pas aux dimensions indiquées dans la déclaration, le compilateur ne peut pas déduire le type de données du tableau. Par exemple, le code suivant génère cette erreur.  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **ID d’erreur :** BC36909  
  
## Voir aussi  
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [NOTINBUILD Comment : initialiser un tableau multidimensionnel](http://msdn.microsoft.com/fr-fr/502dcf8b-d86c-46f1-ad7d-3ce809645774)