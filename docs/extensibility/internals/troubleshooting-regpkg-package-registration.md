---
title: "Inscription de package de RegPkg de r&#233;solution des probl&#232;mes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Inscription de package de RegPkg de r&#233;solution des probl&#232;mes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  La meilleure méthode pour enregistrer des packages dans Visual Studio est en utilisant des fichiers .pkgdef. Ainsi, pour le déploiement de l'extension sans avoir à accéder au Registre système. Pkgdef fichiers sont créés à l'aide de la [Utilitaire de CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Pour enregistrer un package à l'aide de RegPkg dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez utiliser la version de RegPkg qui convient à votre package.  
  
## Versions de RegPkg liées à des Versions de Package  
 Il existe deux versions de RegPkg. Une version est incluse dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cette version permet d'enregistrer des packages qui ont été générés à l'aide d'un des assemblys suivants :  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Il ne peut pas inscrire les packages qui ont été générés à l'aide de l'assembly Microsoft.VisualStudio.Shell.dll antérieures.  
  
 La version antérieure de RegPkg pouvez enregistrer les packages qui ont été générés à l'aide de l'assembly Microsoft.VisualStudio.Shell.dll. Toutefois, il ne peut pas inscrire les packages créés à l'aide des versions ultérieures de cet assembly.  
  
## Voir aussi  
 [Publication d’un produit](../../misc/releasing-a-visual-studio-integration-product.md)