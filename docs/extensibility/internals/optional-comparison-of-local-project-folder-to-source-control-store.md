---
title: Comparer le dossier du projet au magasin de contrôle de code source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726123"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparaison facultative du dossier de projet local avec le magasin de contrôle de code source
Dans l’API de plug-in de contrôle de code source 1,2, la comparaison entre le dossier de projet local et le contrôle de code source s’effectue à l’aide des fonctions [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 Dans **Explorateur de solutions**, si un dossier est sélectionné au lieu d’un fichier individuel, le menu contextuel **comparer les versions** appelle les nouveaux [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [SccDirDiff](../../extensibility/sccdirdiff-function.md) dans le plug-in de contrôle de code source.

## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nouvelles fonctions
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 La fonction `SccDirQueryInfo` est appelée avant `SccDirDiff` pour déterminer si le répertoire de travail est sous contrôle de code source. La fonction `SccDirDiff` affiche les différences entre le répertoire local actuel et le dossier du contrôle de code source correspondant. Cette commande demande au plug-in de contrôle de code source d’afficher la liste des modifications apportées à l’annuaire. Un plug-in de contrôle de code source fournit sa propre interface utilisateur pour afficher les différences.

> [!NOTE]
> Cette fonction utilise les mêmes indicateurs de commande que [SccDiff](../../extensibility/sccdiff-function.md). En tant que fournisseur de plug-in de contrôle de code source, vous pouvez choisir de ne pas prendre en charge l’opération « comparaison rapide » pour les répertoires.

## <a name="see-also"></a>Voir aussi
- [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)