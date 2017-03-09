---
title: "Impossible de sp&#233;cifier un modificateur autorisant les valeurs Null dans les d&#233;clarations de variable avec &#39;As New&#39; | Microsoft Docs"
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
  - "bc33109"
  - "vbc33109"
helpviewer_keywords: 
  - "BC33109"
ms.assetid: 135def20-3535-4239-bffb-43208d1b3f63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de sp&#233;cifier un modificateur autorisant les valeurs Null dans les d&#233;clarations de variable avec &#39;As New&#39;
Le modificateur de type nullable \(?\) a été inclus dans une déclaration de variable où `As New` a été spécifié. L’exemple suivant génère cette erreur :  
  
```vb#  
Dim num? As New ExampleStructure  
```  
  
 **ID d’erreur :** BC33109  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé `New` de la déclaration de variable nullable, comme indiqué dans l’exemple suivant :  
  
    ```vb#  
    Dim num? As ExampleStructure  
    ```  
  
## Voir aussi  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)