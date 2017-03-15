---
title: "Prise en main de Plug-ins de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, mise en route"
  - "mise en route prise en main, contrôle plug-ins de source"
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Prise en main de Plug-ins de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pour créer un plug\-in contrôle de code source, vous devez créer une DLL qui implémente des fonctions définies dans l'API des plug\-ins de contrôle de code source, puis enregistrer la DLL avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour le rendre disponible dans le contrôle de version de code source.  
  
 Trois versions de l'API des plug\-ins de contrôle de code source \(versions 1,1, 1,2, et 1,3\) sont disponibles pour le plug\-ins de contrôle de code source.  L'API des plug\-ins de contrôle de code source documenté ici est la version 1,3.  il a été conçu pour être entièrement compatible avec le plug\-ins de contrôle de code source prenant en charge les versions 1,1 et 1,2.  La section de [Quelles sont les nouveautés dans la Version Source du contrôle plug\-in API 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) détaille les nouvelles fonctionnalités prises en charge dans la version la plus récente de l'API de plug\-in contrôle de code source.  
  
## Dans cette section  
 [Comment : installer un plug\-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Décrit comment créer des entrées du Registre requises pour créer une DLL de contrôle de code source.  
  
 [Quelles sont les nouveautés dans la Version Source du contrôle plug\-in API 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fournit une vue d'ensemble des modifications apportées à l'API des plug\-ins de contrôle de code source dans la version 1,3.  
  
 [Quelles sont les nouveautés dans la Source contrôle plug\-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fournit une vue d'ensemble des modifications apportées à l'API des plug\-ins de contrôle de code source dans la version 1,2.  
  
## Rubriques connexes  
 [Plug\-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments de l'API de plug\-in contrôle de code source.  
  
 [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 définit le plug\-in Kit de développement logiciel de contrôle de code source et décrit les ressources incluses.