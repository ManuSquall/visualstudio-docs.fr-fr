---
title: "MSBuild Error MSB3116 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3116
**MSB3116 : l'application est marquée pour être hébergée dans le navigateur, mais est également pour être utilisée en ligne et hors connexion.  Modifiez votre application pour une utilisation en ligne uniquement.**  
  
 Lorsque vous déployez une application de navigateur Web WPF, vous devez affecter la valeur `True` à la propriété <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>.  Lorsque <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> a la valeur `True`, vous devez affecter la valeur `False` à la propriété <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> \(pour rendre l'installation disponible en ligne uniquement\).  Si cette condition n'est pas remplie, ce message d'erreur s'affiche.  
  
### Pour corriger cette erreur  
  
-   Affectez à la propriété <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> la valeur `False`.  
  
## Voir aussi  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)