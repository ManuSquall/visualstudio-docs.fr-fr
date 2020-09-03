---
title: Utiliser MSBuild.exe pour générer des cibles spécifiques dans des solutions
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 178dfcaf0bdf8296fd271cb7c4e5dd0bbd251d7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633926"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Guide pratique pour générer des cibles spécifiques dans des solutions en utilisant MSBuild.exe

Vous pouvez utiliser *MSBuild.exe* pour générer des cibles spécifiques de certains projets d’une solution.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Pour générer une cible spécifique d’un projet particulier d’une solution

1. Dans la ligne de commande, tapez `MSBuild.exe <SolutionName>.sln`, où `<SolutionName>` correspond au nom de fichier de la solution qui contient la cible à exécuter.

2. Spécifiez la cible après le `-target:` commutateur au format \<ProjectName> : \<TargetName> . Si le nom du projet contient un caractère `%`, `$`, `@`, `;`, `.`, `(`, `)` ou `'`, remplacez-le par un `_` dans le nom de la cible spécifié.

## <a name="example"></a>Exemple

 L’exemple suivant exécute la cible `Rebuild` du projet `NotInSlnFolder`, puis exécute la cible `Clean` du projet `InSolutionFolder`, qui se trouve dans le dossier de solution *NewFolder*.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Dépannage

Si vous voulez examiner les options disponibles, vous pouvez utiliser pour cela une option de débogage fournie par MSBuild. Définissez la variable d’environnement `MSBUILDEMITSOLUTION=1` et générez votre solution. Cela produira un fichier MSBuild nommé * \<SolutionName> . sln. saproj* qui affiche l’affichage interne de MSBuild de la solution au moment de la génération. Vous pouvez inspecter cette vue pour déterminer les cibles disponibles pour la génération.

N’effectuez pas de génération en ayant défini cette variable d’environnement, sauf si vous avez besoin de cette vue interne. Ce paramètre peut provoquer des problèmes de génération des projets dans votre solution.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
