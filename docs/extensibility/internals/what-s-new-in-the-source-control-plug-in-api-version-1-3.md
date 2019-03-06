---
title: Ce que&#39;s dans la Source de contrôle plug-in API Version 1.3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b61e56fcef8bbbe8e9f36a39580eae14ad582d5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645977"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Ce que&#39;s dans la Source de contrôle plug-in API Version 1.3
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
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)