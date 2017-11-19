---
title: "Comparer le dossier de projet pour le magasin de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cde0a7c34fe81c86d9f500bb1800006e5291ee92
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparaison facultatif du dossier de projet Local pour le magasin de contrôle de code Source
Dans la Source de contrôle 1.2 d’API de plug-in de la comparaison entre le dossier de projet local et le contrôle de code source est accomplie en utilisant les fonctions [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Dans **l’Explorateur de solutions**, si un dossier est sélectionné au lieu d’un fichier individuel, le **comparer les versions** menu contextuel appelle la nouvelle [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [ SccDirDiff](../../extensibility/sccdirdiff-function.md) dans le plug-in de contrôle de code source.  
  
## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Le `SccDirQueryInfo` fonction est appelée avant `SccDirDiff` pour déterminer si le répertoire de travail est sous contrôle de code source. Le `SccDirDiff` fonction affiche les différences entre le répertoire local actuel et le dossier de contrôle de source correspondant. Cette commande vous demande le contrôle de source de plug-in pour afficher la liste des modifications à l’annuaire. Un plug-in de contrôle de code source fournit sa propre interface utilisateur pour afficher les différences.  
  
> [!NOTE]
>  Cette fonction utilise les mêmes indicateurs de commande en tant que [SccDiff](../../extensibility/sccdiff-function.md). En tant qu’un fournisseur de plug-in de contrôle source, vous pouvez choisir de ne prend ne pas en charge l’opération « diff rapide » pour les répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)