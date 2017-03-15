---
title: "MSBuild Error MSB3141 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3141
**MSB3141 : Aucun attribut 'PublicKey' ou 'Hash' n'est spécifié pour le fichier '\<fichier\>' dans l'élément '\<package\>'.**  
  
 Cette erreur se produit lorsque vous essayez d'utiliser HomeSite pour les packages de programme d'amorçage.  Toutefois, le manifeste du programme d'amorçage ne contient pas les informations appropriées pour la vérification de fichier \(une clé publique ou un hachage\) au moment de l'exécution.  
  
### Pour corriger cette erreur  
  
-   Téléchargez le fichier de package pour lequel les informations manquent et copiez\-le dans le cache du programme d'amorçage.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)