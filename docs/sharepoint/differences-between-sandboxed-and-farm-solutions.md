---
title: "Diff&#233;rences entre les solutions bac &#224; sable (sandbox) et les solutions de batterie"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "solutions de batterie (développement SharePoint dans Visual Studio)"
  - "solutions bac à sable (sandbox) (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, solutions de batterie"
  - "développement SharePoint dans Visual Studio, solutions bac à sable (sandbox)"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Diff&#233;rences entre les solutions bac &#224; sable (sandbox) et les solutions de batterie
  Lorsque vous compilez une solution SharePoint, elle est déployée sur le serveur SharePoint et un débogueur est joint pour la déboguer.  Le processus utilisé pour déboguer la solution dépend du paramètre de la propriété Solution bac à sable \(sandbox\) : solution bac à sable \(sandbox\) ou solution de batterie.  
  
 Pour plus d'informations, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
## Solutions de batterie  
 Les solutions de batterie, hébergées dans le processus de travail IIS \(W3WP.exe\), exécutent du code qui peut affecter la batterie entière.  Lorsque vous déboguez un projet SharePoint dont la propriété Solution bac à sable \(sandbox\) a la valeur « solution de batterie », le pool d'applications IIS du système est recyclé avant que SharePoint retire ou déploie la fonctionnalité de manière à libérer tous les fichiers verrouillés par le processus de travail IIS.  Seul le pool d'applications IIS qui sert l'URL de site du projet SharePoint est recyclé.  
  
## Solutions bac à sable \(sandbox\)  
 Les solutions bac à sable \(sandbox\), hébergées dans le processus de travail de la solution du code utilisateur SharePoint \(SPUCWorkerProcess.exe\), exécutent du code qui peut affecter uniquement la collection de sites de la solution.  Dans la mesure où les solutions bac à sable \(sandbox\) ne s'exécutent pas dans le processus de travail IIS, il n'est pas nécessaire de redémarrer le pool d'applications IIS ou le serveur IIS.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] joint le débogueur au processus SPUCWorkerProcess que le service SPUserCodeV4 dans SharePoint déclenche et contrôle automatiquement.  Il n'est pas nécessaire de recycler le processus SPUCWorkerProcess pour qu'il charge la version la plus récente de la solution.  
  
## L'un ou l'autre type de solution  
 Avec l'un ou l'autre type de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] joint également le débogueur au navigateur pour permettre le débogage de script côté client.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le moteur de débogage de script à cette fin.  Pour activer le débogage de script, vous devez modifier les paramètres par défaut du navigateur lorsque vous y êtes invité.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] joint uniquement le débogueur aux processus W3WP ou SPUCWorkerProcess exécutant le site actuel.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] joint également les moteurs de débogage de workflow et COM Plus managés.  
  
## Voir aussi  
 [Débogage de solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md)  
  
  