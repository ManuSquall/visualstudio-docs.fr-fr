---
title: Supprimer les informations de contrôle de code source à partir de fichiers .proj et .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 100de838eb1b205046d09d1149d78d3adba43b91
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260810"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Suppression des fichiers d’informations de contrôle de code source .Proj et .Sln
Dans la version 1.2 de l’API de plug-in de contrôle de Source SCC, les informations sont stockées dans un MSSCCPRJ. Fichier de contrôle de code source. L’avantage de la MSSCCPRJ. Fichier de contrôle de code source est que les informations de contrôle de code source n'est pas de source - contrôlé, comme il se trouve dans les fichiers .proj et .sln.

## <a name="version-12-changes"></a>Modifications de la version 1.2
 Dans le contrôle plug-ins de code source qui reposent sur l’API de plug-in de contrôle de Source version 1.1, les informations sur le contrôle de code source sont stockées dans le projet (.proj) et les fichiers solution (.sln). L’emplacement de base de données des informations de contrôle de source est spécifié par le AuxPath et l’emplacement spécifique dans la base de données est spécifié par NomProjet. Ce comportement peut provoquer des problèmes après la branche, branche ou opérations de copie, car le ProjName serait généralement non valide après une de ces opérations.

 Dans l’API de plug-in de contrôle de Source version 1.1, l’IDE utilisée ~ fichiers SAK pour détecter si un plug-in pris en charge la MSSCCPRJ. Méthode de contrôle de code source de stockage des informations de contrôle de source. L’API de plug-in de contrôle de Source version 1.2 fournit une nouvelle fonctionnalité de détection de la prise en charge pour MSSCCPRJ. Fichier de contrôle de code source sans utiliser un ~ les fichier SAK. Pour plus d’informations, consultez [élimination de ~ SAK fichiers](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Voir aussi
- [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)