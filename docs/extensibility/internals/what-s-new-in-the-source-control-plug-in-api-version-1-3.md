---
title: Nouveautés &apos; de l’API de plug-in de contrôle de code source 1,3
description: Découvrez les nouveautés de l’API de plug-in de contrôle de code source version 1,3, qui introduit les nouvelles fonctions pour fournir un contrôle plus avancé.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 491c35a1a99af9b3271e8b2036f7d0c6f8f57908
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487788"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>&#39;nouveautés de l’API de plug-in de contrôle de code source version 1,3
La version 1,3 de l’API de plug-in de contrôle de code source introduit les nouvelles fonctions suivantes pour fournir un contrôle plus avancé.

## <a name="changes"></a>Modifications
 Les fonctions suivantes sont nouvelles dans l’API de plug-in de contrôle de code source version 1,3 :

|Fonction|Vue d’ensemble|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permet de signaler des bits de fonctionnalité supplémentaires|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permet d’examiner les fichiers qui ont des versions plus récentes dans la base de données de contrôle de version que sur le disque local|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permet d’examiner l’état des modifications de nom (renommages, ajouts et suppressions) pour les fichiers spécifiés.|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permet l’examen des répertoires et des fichiers dans la base de données de contrôle de version|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers spécifiée de la base de données de contrôle de version au projet en cours|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Effectue une « récupération » en mode silencieux des fichiers spécifiés (aucune interface utilisateur n’est affichée)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Autorise l’accès aux options spécifiques à l’utilisateur|

## <a name="see-also"></a>Voir aussi
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
