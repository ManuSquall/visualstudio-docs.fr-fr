---
title: "D&#233;pannage des exceptions&#160;: System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "InvalidPipelineStoreException (exception)"
  - "System.AddIn.Hosting.InvalidPipelineStoreException (exception)"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.AddIn.Hosting.InvalidPipelineStoreException
Exception <xref:System.AddIn.Hosting.InvalidPipelineStoreException> renvoyée lorsqu'un répertoire est introuvable et que l'utilisateur ne dispose pas de l'autorisation d'accès au chemin d'accès de la racine du pipeline ou d'un complément.  
  
## Notes  
 Contrairement à <xref:System.IO.DirectoryNotFoundException>, cette exception ne fournit aucune information relative au chemin d'accès. Cela empêche tout utilisateur malveillant de spécifier délibérément des chemins d'accès erronés et d'utiliser les informations retournées par l'exception pour déterminer des chemins d'accès réels.  
  
 L'exception est renvoyée par les méthodes de découverte suivantes qui génèrent et mettent à jour le magasin d'informations de complément et de pipeline : <xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>, <xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Update%2A> et <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>.  
  
## Voir aussi  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)