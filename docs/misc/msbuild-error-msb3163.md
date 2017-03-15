---
title: "MSBuild Error MSB3163 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3163
**MSB3163 : Le paramètre d'entrée de génération 'ComponentsLocation\=\<EmplacementComposants\>' n'est pas valide.  La valeur doit être 'HomeSite', 'Relative' ou 'Absolute'.  La valeur 'HomeSite' sera utilisée.**  
  
 Cette erreur se produit lorsque la valeur spécifiée pour la propriété `ComponentsLocation` \(emplacement à partir duquel les composants requis sont installés\) n'est pas valide.  `ComponentsLocation` doit correspondre à l'une des trois valeurs suivantes : `HomeSite`, `Relative` ou `Absolute`.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)