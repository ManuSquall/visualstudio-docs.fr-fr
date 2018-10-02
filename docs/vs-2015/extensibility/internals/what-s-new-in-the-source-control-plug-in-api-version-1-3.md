---
title: Ce que&#39;s dans la Source de contrôle plug-in API Version 1.3 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5e8e5fd761cbd8c1baf2b75160010f19a8430cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495762"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Ce que&#39;s dans la Source de contrôle plug-in API Version 1.3
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [que&#39;Nouveautés de Version 1.3 des API de plug-in de contrôle Source](https://docs.microsoft.com/visualstudio/extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3).  
  
L’API de plug-in de contrôle de Source version 1.3 présente les nouvelles fonctions suivantes pour fournir un contrôle plus avancée.  
  
## <a name="changes"></a>Modifications  
 Les fonctions suivantes sont nouvelles pour l’API de plug-in de contrôle de Source version 1.3 :  
  
|Fonction|Vue d'ensemble|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permet les bits de capacité supplémentaires soient signalés|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permet l’examen des fichiers qui ont des versions plus récentes de la base de contrôle de version que sur le disque local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permet l’examen de l’état de changements de nom (, ajouts et suppressions) pour les fichiers spécifiés|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permet l’examen des répertoires et des fichiers dans la base de données de contrôle de version|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers spécifiée à partir de la base de données de contrôle de version pour le projet actuel|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Effectue un sans assistance « Get » des fichiers spécifiés (aucune interface utilisateur n’est affiché)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permet d’accéder aux options spécifiques à l’utilisateur|  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

