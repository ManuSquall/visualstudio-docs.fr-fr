---
title: "D&#233;pannage des exceptions&#160;: System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeploymentDownloadException (classe)"
  - "déploiement d’applications [C#], classe DeploymentDownloadException"
  - "déployer des applications [C#], classe DeploymentDownloadException"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.DeploymentFramework.DeploymentDownloadException
Une `T:System.DeploymentFramework.DeploymentDownloadException` est levée si une exception réseau d'un type quelconque se produit lorsqu'une mise à jour d'application est téléchargée.  
  
## Conseils associés  
 **Examinez InnerException pour déterminer l'exception System.Net ou System.IO sous\-jacente.**  
 Cette exception se produit toutes les fois qu'une exception réseau est levée lors du téléchargement d'une mise à jour d'application. Examinez la propriété <xref:System.Exception.InnerException%2A> de l'exception pour déterminer l'exception sous\-jacente.  
  
## Voir aussi  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)