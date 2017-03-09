---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
Le système de projet ne peut pas créer l'outil personnalisé.  L'outil personnalisé demandé ne sera pas exécuté, car le système de projet n'a aucun moyen de l'instancier.  Vérifiez que l'outil personnalisé est correctement installé et inscrit.  
  
 Cette erreur peut avoir été provoquée par le fait que vous avez spécifié un nom d'outil personnalisé non valide pour la propriété `CustomTool` d'un fichier donné.  Il est également possible que le fichier projet \(.vbproj\/.csproj\) ait été modifié, rendant la valeur de la propriété `CustomTool` non valide.  Il se peut aussi que vous utilisiez un projet développé sur un autre ordinateur, disposant de l'outil personnalisé, mais que ce dernier ne soit pas installé sur votre ordinateur.  Pour plus d'informations sur la propriété `CustomTool`, consultez [File Properties](http://msdn.microsoft.com/fr-fr/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 Cette erreur peut également se produire si [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) échoue pour l'outil personnalisé.  Il se peut par exemple qu'il n'ait pas été inscrit ou qu'une DLL nécessaire soit manquante.  
  
## Voir aussi  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)