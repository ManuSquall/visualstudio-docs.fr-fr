---
title: "Comparez les dossiers de projet pour le magasin de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: b2ed6955e5ba6fa334cc89a0c2ea8a3d4248f362
ms.lasthandoff: 02/22/2017

---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparaison facultatif du dossier de projet Local vers le magasin de contrôle de code Source
Dans la Source de contrôle 1.2 API de plug-in de la comparaison entre le dossier de projet local et le contrôle de code source s’effectue en utilisant les fonctions [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Dans **l’Explorateur de solutions**, si un dossier est sélectionné au lieu d’un fichier individuel, le **comparer les versions** menu contextuel appelle la nouvelle [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [SccDirDiff](../../extensibility/sccdirdiff-function.md) dans le plug-in de contrôle de code source.  
  
## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Le `SccDirQueryInfo` fonction est appelée avant `SccDirDiff` pour déterminer si le répertoire de travail est sous contrôle de code source. Le `SccDirDiff` fonction affiche les différences entre le répertoire local actuel et le dossier de contrôle de code source correspondant. Cette commande vous demande le contrôle de code source du plug-in pour afficher la liste des modifications apportées à l’annuaire. Un plug-in de contrôle de code source fournit sa propre interface utilisateur pour afficher les différences.  
  
> [!NOTE]
>  Cette fonction utilise les mêmes indicateurs de commande en tant que [SccDiff](../../extensibility/sccdiff-function.md). Fournisseur du plug-in de contrôle source, vous pouvez choisir de ne prend ne pas en charge l’opération « diff rapide » pour les répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés dans la Source contrôle plug-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
