---
title: "MSBuild Error MSB3127 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3127
**MSB3127 : L'icône par défaut \<NomIcône\> est introuvable dans les références de fichier actuelles ou ne fait pas partie du groupe de téléchargement requis.  Le nom de fichier de l'icône par défaut respecte la casse ; par conséquent, le nom de fichier référencé dans le manifeste d'application doit correspondre exactement au nom de fichier de l'icône.**  
  
 Lorsque vous publiez une application configurée pour utiliser des associations de fichiers, l'icône par défaut référencée dans le manifeste doit se trouver dans les références de fichier actuelles ou faire partie du groupe de téléchargement requis.  L'icône par défaut est l'icône qui apparaît pour les fichiers qui présentent l'association de fichier configurée \(l'extension de nom de fichier configurée\).  
  
### Pour corriger cette erreur  
  
-   Ajoutez le fichier icône au projet actuel et incluez\-le dans le groupe de téléchargement requis.  Pour plus d'informations, consultez [How to: Specify Which Files Are Published by ClickOnce](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md).  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)