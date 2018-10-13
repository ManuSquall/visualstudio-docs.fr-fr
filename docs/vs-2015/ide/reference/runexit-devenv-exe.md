---
title: -Runexit (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86a99aed7876454d09e5bb0157f6dcaaa7fb4072
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242255"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Compile et exécute la solution ou le projet spécifié, puis ferme l’environnement de développement intégré (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Arguments  
 `SolutionName`  
 Obligatoire. Chemin complet et nom d’un fichier solution.  
  
 `ProjectName`  
 Obligatoire. Chemin complet et nom d’un fichier projet.  
  
## <a name="remarks"></a>Notes  
 Compile et exécute la solution ou le projet spécifié en fonction des paramètres spécifiés pour la configuration de la solution active. Ce commutateur réduit la fenêtre de l’IDE pendant l’exécution de la solution ou du projet et ferme cette fenêtre à la fin de leur exécution.  
  
-   Placez entre guillemets doubles les chaînes contenant des espaces.  
  
-   Les informations résumées, notamment les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## <a name="example"></a>Exemple  
 Cet exemple exécute la solution `MySolution` dans une fenêtre réduite de l’IDE en utilisant la configuration de déploiement active, puis ferme l’IDE.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



