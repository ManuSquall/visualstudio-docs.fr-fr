---
title: "MSBuild Error MSB3128 | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3128
**MSB3128 : Les manifestes ClickOnce ne peuvent pas être signés car ils contiennent une ou plusieurs références qui ne sont pas hachées.**  
  
 Lorsque vous publiez une application disposant d'un manifeste signé, tous les fichiers doivent être inclus dans le hachage.  
  
### Pour corriger cette erreur  
  
1.  Accédez à la page **Publier** du **Concepteur de projets**.  
  
2.  Cliquez sur **Fichiers d'application**.  
  
3.  Affectez la valeur **Inclure** à **Hachage** pour tous les fichiers à publier.  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)