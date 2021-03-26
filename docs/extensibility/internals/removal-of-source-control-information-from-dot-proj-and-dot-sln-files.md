---
title: Supprimer les informations de contrôle de code source des fichiers. projet. sln
description: Dans l’API de plug-in de contrôle de code source, les informations SCC sont stockées dans un MSSCCPRJ. Fichier SCC à la place des fichiers de projet et de solution.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fd4b4f12ab819903408d4d895773664e892b3ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069385"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Suppression des informations de contrôle de code source des fichiers. projet. sln

Dans la version 1,2 de l’API de plug-in de contrôle de code source, les informations SCC sont stockées dans un MSSCCPRJ. Fichier SCC. L’avantage du MSSCCPRJ. Le fichier SCC est que les informations SCC ne sont pas sous contrôle de code source, comme dans les fichiers. projet. sln.

## <a name="version-12-changes"></a>Modifications de la version 1,2

 Dans les plug-ins de contrôle de code source basés sur la version 1,1 de l’API de plug-in de contrôle de code source, les informations sur le contrôle de code source sont stockées dans les fichiers de projet (. proj) et de solution (. sln). L’emplacement de la base de données des informations de contrôle de code source est spécifié par AuxPath, et l’emplacement spécifique dans la base de données est spécifié par ProjName. Ce comportement peut provoquer des problèmes après les opérations de branche, de branchement ou de copie, car le ProjName n’est généralement pas valide après l’une de ces opérations.

 Dans la version 1,1 de l’API de plug-in de contrôle de code source, l’IDE utilisait des fichiers ~ SAK pour détecter si un plug-in prenait en charge le fichier MSSCCPRJ. Méthode SCC de stockage des informations de contrôle de code source. La version 1,2 de l’API de plug-in de contrôle de code source offre une nouvelle fonctionnalité de détection de la prise en charge de MSSCCPRJ. Fichier SCC sans utiliser de fichier ~ SAK. Pour plus d’informations, consultez [élimination des fichiers ~ SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Voir aussi

- [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
