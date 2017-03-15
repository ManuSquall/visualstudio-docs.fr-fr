---
title: "MSBuild Error MSB3180 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3180
**MSB3180 : Le composant COM '\<assembly\>' est défini à la fois dans '\<fichier\>' et '\<fichier\>', clsid\/tlbid\="'\<assembly\>'".**  
  
 Cette erreur est générée par le processus de génération du manifeste de l'application lorsque les références COM en double \(aux classes ou bibliothèques de types\) sont contenues dans les références de fichier ou dans les manifestes dépendants.  
  
 Par exemple, vous pouvez recevoir cette erreur si vous avez ajouté une référence à un objet COM avec un manifeste externe et une référence au même objet COM avec un manifeste interne.  
  
### Pour corriger cette erreur  
  
-   Supprimez l'une des références COM en double.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)