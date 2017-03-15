---
title: "Impossible d’obtenir le nom complet du syst&#232;me d’exploitation en raison d’une erreur interne | Microsoft Docs"
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
  - "vbrDiagnosticInfo_FullOSName"
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’obtenir le nom complet du syst&#232;me d’exploitation en raison d’une erreur interne
Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne. Ceci peut être dû au fait que WMI est absent de l’ordinateur actuel.  
  
 Un appel à la propriété `My.Computer.Info.OSFullName` a échoué. WMI \(Windows Management Instrumentation\) n’est peut\-être pas installé sur l’ordinateur actuel.  
  
### Pour corriger cette erreur  
  
1.  Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété `My.Computer.Info.OSFullName`.  
  
2.  Pour plus d’informations sur WMI et comment l’installer, accédez à la page  et recherchez « Windows Management Instrumentation Core ».  
  
## Voir aussi  
 [My.Computer.Info.OSFullName, propriété](http://msdn.microsoft.com/fr-fr/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Gestion des exceptions et des erreurs en Visual Basic](http://msdn.microsoft.com/fr-fr/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)