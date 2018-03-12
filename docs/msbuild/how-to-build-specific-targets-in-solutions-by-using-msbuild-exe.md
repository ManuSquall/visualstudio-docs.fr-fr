---
title: "Comment : générer des cibles spécifiques dans des solutions en utilisant MSBuild.exe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4437c8030f66ae24d94a83d796c0d0edf7e59c79
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Comment : générer des cibles spécifiques dans des solutions en utilisant MSBuild.exe
Vous pouvez utiliser MSBuild.exe pour générer des cibles spécifiques de certains projets d’une solution.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Pour générer une cible spécifique d’un projet particulier d’une solution  
  
1.  Dans la ligne de commande, tapez `MSBuild.exe <SolutionName>.sln`, où `<SolutionName>` correspond au nom de fichier de la solution qui contient la cible à exécuter.  
  
2. Spécifiez la cible après le commutateur `/target:` selon le format **`ProjectName`**`:`**`TargetName`**. Si le nom du projet contient un caractère `%`, `$`, `@`, `;`, `.`, `(`, `)` ou `'`, remplacez-le par un `_` dans le nom de la cible spécifié.
  
## <a name="example"></a>Exemple  
 L’exemple suivant exécute la cible `Rebuild` du projet `NotInSlnFolder`, puis exécute la cible `Clean` du projet `InSolutionFolder`, qui se trouve dans le dossier de solution `NewFolder`.  
  
```
msbuild SlnFolders.sln /target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean`
```

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous voulez examiner les options disponibles, vous pouvez utiliser pour cela une option de débogage fournie par MSBuild. Définissez la variable d’environnement `MSBUILDEMITSOLUTION=1` et générez votre solution. Cette opération génère un fichier MSBuild nommé `<SolutionName>.sln.metaproj`, qui montre une vue interne de MSBuild de la solution au moment de la génération. Vous pouvez inspecter cette vue pour déterminer les cibles disponibles pour la génération.

N’effectuez pas de génération en ayant défini cette variable d’environnement, sauf si vous avez besoin de cette vue interne. Ce paramètre peut provoquer des problèmes de génération des projets dans votre solution.

## <a name="see-also"></a>Voir aussi  
 [Command-Line Reference (Référence de ligne de commande MSBuild)](../msbuild/msbuild-command-line-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)
