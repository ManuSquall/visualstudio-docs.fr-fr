---
title: Comparaison facultative du dossier de projet Local à Source contrôle Store | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6806a01127250b2376fee0aa77d55554eeba9bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506008"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparaison facultative du dossier de projet local avec le magasin de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [comparer de dossier de projet pour Source contrôle Store](https://docs.microsoft.com/visualstudio/extensibility/internals/optional-comparison-of-local-project-folder-to-source-control-store).  
  
Dans la Source de contrôle 1.2 d’API de plug-in de la comparaison entre le dossier de projet local et le contrôle de code source s’effectue en utilisant les fonctions [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Dans **l’Explorateur de solutions**, si un dossier est sélectionné au lieu d’un fichier individuel, le **comparer les versions** menu contextuel appelle la nouvelle [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) et [ SccDirDiff](../../extensibility/sccdirdiff-function.md) dans le plug-in de contrôle de code source.  
  
## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Le `SccDirQueryInfo` fonction est appelée avant `SccDirDiff` pour déterminer si le répertoire de travail est sous contrôle de code source. Le `SccDirDiff` fonction affiche les différences entre le répertoire local actuel et le dossier de contrôle de source correspondant. Cette commande vous demande le plug-in pour afficher la liste des modifications dans le répertoire de contrôle de code source. Un plug-in de contrôle de code source fournit sa propre interface utilisateur pour afficher les différences.  
  
> [!NOTE]
>  Cette fonction utilise les mêmes indicateurs de commande en tant que [SccDiff](../../extensibility/sccdiff-function.md). En tant qu’un fournisseur de plug-in de contrôle source, vous pouvez choisir de ne prend ne pas en charge l’opération de « diff rapide » pour les répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

