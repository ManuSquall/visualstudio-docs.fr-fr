---
title: "Impossible d’obtenir un flux pour le journal | Microsoft Docs"
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
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’obtenir un flux pour le journal
Impossible d’obtenir un flux pour le journal. Les noms de fichiers potentiels basés sur \<nom\> sont déjà en cours d’utilisation.  
  
 La classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> n’a pas pu créer un nouveau fichier journal car tous les noms de fichier journal potentiels basés sur \<nom\> sont déjà en cours d’utilisation.  
  
 Un nombre trop élevé de fichiers journaux peut indiquer un problème architectural avec l’application. Pour plus d’informations, consultez la documentation de la classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>.  
  
### Pour corriger cette erreur  
  
1.  Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> la valeur <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> pour inclure un horodatage dans le nom du fichier journal.  
  
2.  Archivez les journaux existants et supprimez\-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer de nouveaux journaux.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [My.Application.Log, objet](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)