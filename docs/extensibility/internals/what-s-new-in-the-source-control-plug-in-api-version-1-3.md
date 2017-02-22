---
title: "Quelles sont les nouveaut&#233;s dans la Version Source du contr&#244;le plug-in API 1.3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de source de plug-ins, quelles sont les nouveautés dans les API v1.3"
  - "Quel est le nouveau Visual Studio SDK, source plug-ins de contrôle"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Quelles sont les nouveaut&#233;s dans la Version Source du contr&#244;le plug-in API 1.3
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La version du plug\-in 1,3 d'API de contrôle de code source introduit de nouvelles fonctions suivantes pour fournir un contrôle plus avancé.  
  
## modifications  
 Les fonctions suivantes sont nouveaux dans la version du plug\-in 1,3 d'API de contrôle de code source :  
  
|Fonction|Vue d'ensemble|  
|--------------|--------------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permet les bits supplémentaires de fonction à stocker|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permet la révision des fichiers qui ont des versions plus récentes de la base de données de contrôle de version que sur le disque local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permet la révision de l'état des modifications de nom \(le renomme, des ajouts, et les suppressions\) pour les fichiers spécifiés|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permet la révision des répertoires et des fichiers dans la base de données de contrôle de version|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers spécifiée de la base de données de contrôle de version au projet en cours|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Effectue un « get » silencieux des fichiers spécifiés \(aucune interface utilisateur n'est affichée\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permet d'accéder aux options spécifiques à l'utilisateur|  
  
## Voir aussi  
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Quelles sont les nouveautés dans la Source contrôle plug\-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)