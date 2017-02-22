---
title: "Suppression des informations de contr&#244;le de code Source. Proj et. Fichiers sln | Microsoft Docs"
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
  - "plug-ins de contrôle de code source, les fichiers .sln et .proj"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Suppression des informations de contr&#244;le de code Source. Proj et. Fichiers sln
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans la version 1,2 de l'API des plug\-ins de contrôle de code source les informations de SCC sont stockées dans un fichier de MSSCCPRJ.SCC.  L'avantage du fichier de MSSCCPRJ.SCC est que les informations de SCC ne sont pas sous contrôle de code source, comme c'est dans les fichiers de .proj et .sln.  
  
## modifications de la version 1,2  
 Dans le plug\-ins de contrôle de code source qui sont basés sur la version du plug\-in 1,1 d'API de contrôle de code source, les informations relatives au contrôle de code source sont stockées dans les fichiers du projet \(.proj\) et de solution \(.sln\).  L'emplacement de base de données des paramètres de contrôle de code source est spécifié par l'AuxPath, et l'emplacement spécifique dans la base de données est spécifié par Nomprojet.  Ce comportement peut provoquer des problèmes après branche, répliquer, ou copier des opérations car le Nomprojet est généralement valide après l'un de ces opérations.  
  
 Dans la version du plug\-in 1,1 d'API de contrôle de code source, l'IDE a utilisé des fichiers de ~SAK pour déterminer si un plug\-in prenait en charge la méthode de MSSCCPRJ.SCC de stocker des paramètres de contrôle de code source.  La version du plug\-in 1,2 d'API de contrôle de code source fournit une nouvelle fonction pour détecter la prise en charge du fichier de MSSCCPRJ.SCC sans utiliser un fichier de ~SAK.  Pour plus d'informations, consultez [Élimination de ~ SAK fichiers](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## Voir aussi  
 [Quelles sont les nouveautés dans la Source contrôle plug\-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)