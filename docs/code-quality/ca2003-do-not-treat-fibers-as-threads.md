---
title: "CA2003&#160;: Ne traitez pas les fibres comme des threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2003&#160;: Ne traitez pas les fibres comme des threads
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|Catégorie|Microsoft.Reliability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un thread managé est traité comme un thread Win32.  
  
## Description de la règle  
 Ne partez pas du principe qu'un thread managé est un thread Win32.  C'est une fibre.  CLR \(Common Language Runtime\) exécute les threads managés en tant que fibres sur les threads réels appartenant à SQL.  Ces threads peuvent être partagés sur plusieurs AppDomains ainsi que dans des bases de données dans le processus SQL Server.  Le stockage local des threads managés fonctionnera, mais vous ne pourrez pas procéder à un stockage local des threads non managés ou tenter de réexécuter le code sur le système d'exploitation actuel.  Ne modifiez pas les paramètres tels que les paramètres régionaux du thread.  N'appelez pas CreateCriticalSection ou CreateMutex par le biais de P\/Invoke puisqu'ils exigent que le thread qui accède à un verrou doit également quitter le verrou.  Ce cas étant impossible avec l'utilisation de fibres, les sections critiques et les mutex Win32 n'auront aucune utilité dans SQL.  Vous pourrez en toute sécurité exploiter la majeure partie de l'état d'un objet System.Thread managé.  Cela comprend le stockage local des threads managés et la culture du thread actif de l'interface utilisateur.  Cependant, pour des raisons de modèle de programmation, vous ne pourrez pas modifier la culture actuelle d'un thread lorsque vous utiliserez SQL ; vous devrez pour cela bénéficier d'une nouvelle autorisation.  
  
## Comment corriger les violations  
 Examinez votre utilisation des threads et modifiez votre code en conséquence.  
  
## Quand supprimer les avertissements  
 Vous ne devez pas supprimer cette règle.