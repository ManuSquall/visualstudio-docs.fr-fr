---
title: "La valeur de &lt;nom_argument&gt; doit &#234;tre un nombre positif | Microsoft Docs"
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
  - "vbrApplicationLog_NegativeNumber"
ms.assetid: 597c412c-499e-49d2-b656-af2d90c292a5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La valeur de &lt;nom_argument&gt; doit &#234;tre un nombre positif
La valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> doit être supérieure à zéro.  
  
 La propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> spécifie, en octets, la quantité d’espace disque libre nécessaire pour que les messages puissent être écrits dans le fichier journal.  
  
### Pour corriger cette erreur  
  
-   Affectez une valeur positive à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>   
 [My.Application.Log, objet](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)