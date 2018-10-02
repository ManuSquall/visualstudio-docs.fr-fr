---
title: 'Comment : générer des cibles spécifiques dans des solutions en utilisant MSBuild.exe | Microsoft Docs'
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
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bdc5d824d802916c38ef0267dae0de85e8814e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493082"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Comment : générer des cibles spécifiques dans des solutions en utilisant MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : générer des cibles spécifiques dans des Solutions en utilisant MSBuild.exe](https://docs.microsoft.com/visualstudio/msbuild/how-to-build-specific-targets-in-solutions-by-using-msbuild-exe).  
  
  
Vous pouvez utiliser MSBuild.exe pour générer des cibles spécifiques de certains projets d’une solution.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Pour générer une cible spécifique d’un projet particulier d’une solution  
  
1.  Dans la ligne de commande, tapez `MSBuild.exe <SolutionName>.sln`, où `<SolutionName>` correspond au nom de fichier de la solution qui contient la cible à exécuter.  
  
2.  Spécifiez la cible après le commutateur **/t** en respectant le format *nom_projet*:*nom_cible*.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant exécute la cible `Rebuild` du projet `NotInSlnFolder`, puis exécute la cible `Clean` du projet `InSolutionFolder`, qui se trouve dans le dossier de solution `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Command-Line Reference (Référence de ligne de commande MSBuild)](../msbuild/msbuild-command-line-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)


