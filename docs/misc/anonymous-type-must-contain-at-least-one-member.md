---
title: "Le type anonyme doit contenir au moins un membre | Microsoft Docs"
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
  - "bc36574"
  - "vbc36574"
helpviewer_keywords: 
  - "BC36574"
ms.assetid: fdc8dd47-ea38-49e8-8dd5-676f726cd101
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type anonyme doit contenir au moins un membre
La liste d’initialiseurs dans une déclaration de type anonyme ne peut pas être vide.  
  
```  
' Not valid. ' Dim anonInstance = New With {}  
```  
  
 **ID d’erreur :** BC36574  
  
### Pour corriger cette erreur  
  
-   Déclarez un membre entre les accolades, comme illustré dans le code suivant.  
  
    ```  
    Dim anonInstance = New With {.MemberName = "value"}  
    ```  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)