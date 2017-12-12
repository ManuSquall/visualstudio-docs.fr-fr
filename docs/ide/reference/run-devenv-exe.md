---
title: -Run (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5be97e75ac7dc29a6dd0244293259bcd17591233
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Compile et exécute la solution ou le projet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Arguments  
 `SolutionName`  
 Obligatoire. Chemin complet et nom d’un fichier solution.  
  
 `ProjectName`  
 Obligatoire. Chemin complet et nom d’un fichier projet.  
  
## <a name="remarks"></a>Remarques  
 Compile et exécute la solution ou le projet spécifié en fonction des paramètres spécifiés pour la configuration de la solution active. Ce commutateur lance l’environnement de développement intégré (IDE) et le maintient actif à la fin de l’exécution du projet ou de la solution.  
  
-   Placez entre guillemets doubles les chaînes contenant des espaces.  
  
-   Les informations résumées, notamment les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## <a name="example"></a>Exemple  
 Cet exemple exécute la solution `MySolution` en utilisant la configuration de déploiement active.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)