---
title: "Les m&#233;thodes partielles doivent &#234;tre d&#233;clar&#233;es &#39;Private&#39; | Microsoft Docs"
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
  - "vbc31432"
  - "bc31432"
helpviewer_keywords: 
  - "BC31432"
ms.assetid: 3a4474d9-661e-4793-9624-30cf81faddcf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes partielles doivent &#234;tre d&#233;clar&#233;es &#39;Private&#39;
Le modificateur d’accès `Private` est nécessaire dans les déclarations de méthode partielle. L’exemple suivant illustre l’utilisation de `Private` dans la signature de méthode et son implémentation.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **ID d’erreur :** BC31432  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Private` avant `Sub` dans la signature et les déclarations d’implémentation.  
  
## Voir aussi  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)