---
title: Qu’est-ce&#39;nouveau dans la version plug-in de contrôle source API 1.3 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703361"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Qu’est-ce&#39;nouveau dans la version plug-in de contrôle source API 1.3
La version API 1.3 de contrôle source introduit les nouvelles fonctions suivantes pour fournir un contrôle plus avancé.

## <a name="changes"></a>Modifications
 Les fonctions suivantes sont nouvelles dans la version API de contrôle source 1.3 :

|Fonction|Vue d'ensemble|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permet de signaler des bits de capacité supplémentaires|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permet l’examen des fichiers qui ont des versions plus nouvelles dans la base de données de contrôle de version que sur le disque local|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permet l’examen de l’état des changements de nom (renommeurs, ajouts et suppressions) pour les fichiers spécifiés|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permet l’examen des répertoires et des fichiers dans la base de données de contrôle de version|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste spécifiée de fichiers de la base de données de contrôle de version au projet actuel|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Effectue un "Get" silencieux des fichiers spécifiés (aucune interface utilisateur n’est affichée)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permet l’accès à des options spécifiques à l’utilisateur|

## <a name="see-also"></a>Voir aussi
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
