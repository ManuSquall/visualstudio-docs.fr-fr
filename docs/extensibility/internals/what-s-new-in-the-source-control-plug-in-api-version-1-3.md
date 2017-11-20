---
title: "Quel &#39; s de la Source de plug-in API Version 1.3 du contrôle | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd0c23258034fb99f5e2e4e0c86ca9e61c3d68ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Quel &#39; s Source contrôle plug-in API version 1.3
L’API de plug-in de contrôle de Source de version 1.3 introduit les nouvelles fonctions suivantes pour fournir un contrôle plus avancée.  
  
## <a name="changes"></a>Modifications  
 Les fonctions suivantes sont nouvelles pour l’API de plug-in de contrôle de Source de version 1.3 :  
  
|Fonction|Vue d'ensemble|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permet de bits des fonctions supplémentaires doivent être déclarées|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permet l’examen des fichiers qui ont des versions plus récentes de la base de contrôle de version que sur le disque local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permet l’examen de l’état de changements de nom (changements de noms, les ajouts et suppressions) pour les fichiers spécifiés|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permet l’examen des répertoires et des fichiers dans la base de données de contrôle de version|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste spécifiée des fichiers à partir de la base de données de contrôle de version pour le projet actuel|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Effectue un sans assistance « Get » des fichiers spécifiés (sans interface utilisateur est affiché)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permet d’accéder à des options spécifiques à l’utilisateur|  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)