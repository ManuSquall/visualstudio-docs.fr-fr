---
title: "MSBuild Error MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3486
**MSB3486 : Impossible d'obtenir un certificat du magasin '\<MagasinCertificats\>'.**  
  
 La tâche MSBuild `ResolveKeySource` génère cette erreur lorsque le certificat correspondant à l'empreinte du fichier .pfx de votre projet ne figure pas dans votre magasin de certificats personnel.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que l'empreinte du fichier .pfx de votre projet correspond à celle du certificat dans votre magasin de certificats personnel.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)