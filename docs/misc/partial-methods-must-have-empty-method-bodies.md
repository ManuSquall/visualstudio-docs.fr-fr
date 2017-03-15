---
title: "Les m&#233;thodes partielles doivent avoir des corps de m&#233;thodes vides | Microsoft Docs"
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
  - "bc31435"
  - "vbc31435"
helpviewer_keywords: 
  - "BC31435"
ms.assetid: 279f283d-ce40-401c-8494-4bf06394fdd3
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes partielles doivent avoir des corps de m&#233;thodes vides
Le corps d’une déclaration de signature de méthode partielle ne doit pas contenir de code. L’exemple suivant illustre une signature de méthode partielle et son implémentation.  
  
```  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **ID d’erreur :** 31435  
  
### Pour corriger cette erreur  
  
-   Supprimez tout le code de la déclaration de méthode partielle.  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)