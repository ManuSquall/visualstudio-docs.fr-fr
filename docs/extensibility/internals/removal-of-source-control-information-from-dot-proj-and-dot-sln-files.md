---
title: Supprimer les informations de contrôle des sources à partir de fichiers .proj et .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705589"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Suppression des fichiers d’informations de contrôle de code source .Proj et .Sln
Dans la version 1.2 de l’API de contrôle des sources, les informations du CSC sont stockées dans un MSSCCPRJ. Fichier CSC. L’avantage du MSSCCPRJ. Le fichier SCC est que les informations de SCC ne sont pas contrôlées par la source, comme elles l’sont dans les fichiers .proj et .sln.

## <a name="version-12-changes"></a>Version 1.2 Modifications
 Dans les plug-ins de contrôle source qui sont basés sur la version API de contrôle source 1.1, les informations sur le contrôle des sources sont stockées dans le projet (.proj) et les fichiers de solution (.sln). L’emplacement de la base de données des informations de contrôle source est spécifié par LesPath, et l’emplacement spécifique dans la base de données est spécifié par ProjName. Ce comportement peut causer des problèmes après branche, fourchette ou copier les opérations parce que le ProjName serait généralement invalide après l’une de ces opérations.

 Dans la version API de contrôle source 1.1, l’IDE a utilisé des fichiers SAK pour détecter si un plug-in a pris en charge le MSSCCPRJ. Méthode SCC de stockage des informations de contrôle des sources. La version API plug-in source de contrôle 1.2 fournit une nouvelle capacité de détection du support pour MSSCCPRJ. Fichier SCC sans utiliser de fichier SAK. Pour plus d’informations, voir [Élimination des fichiers SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Voir aussi
- [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
