---
title: "Impossible d’obtenir des informations sur la m&#233;moire en raison d’une erreur interne | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_Memory"
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’obtenir des informations sur la m&#233;moire en raison d’une erreur interne
Un appel à l’une des propriétés d’informations sur la mémoire de l’objet `My.Computer.Info` a échoué.  
  
### Pour corriger cette erreur  
  
-   Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété d’informations sur la mémoire de l’objet `My.Computer.Info`.  
  
## Voir aussi  
 [My.Computer.Info Object](/dotnet/visual-basic/language-reference/objects/my-computer-info-object)   
 [Gestion des exceptions et des erreurs en Visual Basic](http://msdn.microsoft.com/fr-fr/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)