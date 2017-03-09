---
title: "MSBuild Error MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3481
**MSB3481 : Impossible de trouver le certificat de signature.  Vérifiez qu'il se trouve dans le magasin personnel de l'utilisateur actuel.**  
  
 Cette erreur est générée lorsque le certificat de signature ne figure pas dans votre magasin de certificats personnel.  Elle est semblable à [MSBuild Error MSB3486](../misc/msbuild-error-msb3486.md), qui signifie que le certificat a été trouvé, mais ne correspond pas.  
  
### Pour corriger cette erreur  
  
-   Vérifiez qu'un certificat valide qui correspond au fichier .pfx de votre projet est présent dans votre magasin de certificats personnel.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)