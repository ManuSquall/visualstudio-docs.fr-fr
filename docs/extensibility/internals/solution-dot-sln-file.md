---
title: Solution (. Sln) fichier
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705329"
---
# <a name="solution-sln-file"></a>Fichier solution (.sln)

Une solution est une structure pour l’organisation de projets en Visual Studio. La solution conserve les informations de l’Etat pour les projets dans deux dossiers :

- .sln fichier (basé sur le texte, partagé)

- .suo fichier (binaire, options de solution spécifiques à l’utilisateur)

Pour plus d’informations sur les fichiers .suo, voir [Options utilisateur de solution (. Suo) Fichier](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Si votre VSPackage est chargé à la suite d’être référencé dans le fichier .sln, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> à lire dans le fichier .sln.

Le fichier .sln contient des informations textuelles que l’environnement utilise pour trouver et charger les paramètres de valeur nominale pour les données persistantes et le projet VSPackages qu’il fait référence. Lorsqu’un utilisateur ouvre une solution, `preSolution` `Project`l’environnement parcourt le fichier .sln et `postSolution` les informations dans le fichier .sln pour charger la solution, les projets dans la solution et toute information persistante attachée à la solution.

Le dossier de chaque projet contient des informations supplémentaires lues par l’environnement pour remplir la hiérarchie avec les éléments de ce projet. La persistance des données de hiérarchie est contrôlée par le projet. Les données ne sont normalement pas stockées dans le fichier .sln, bien que vous puissiez écrire intentionnellement des informations de projet sur le fichier .sln si vous choisissez de le faire. Pour plus d’informations sur la persistance, voir [La persistance du projet](../../extensibility/internals/project-persistence.md) et [l’ouverture et l’économie des éléments du projet](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>En-tête de fichier

L’en-tête d’un fichier .sln ressemble à ceci:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Définitions

`Microsoft Visual Studio Solution File, Format Version 12.00`\
En-tête standard qui définit la version format de fichier.

`# Visual Studio 15`\
La version principale de Visual Studio qui (plus récemment) a enregistré ce fichier de solution. Ces informations contrôlent le numéro de version dans l’icône de la solution.

`VisualStudioVersion = 15.0.26730.15`\
La version complète de Visual Studio qui (plus récemment) a enregistré le fichier de solution. Si le fichier de solution est enregistré par une version plus récente de Visual Studio qui a la même version majeure, cette valeur n’est pas mise à jour de manière à réduire le taux de désabonnement dans les fichiers de solutions.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La version minimale (la plus ancienne) de Visual Studio qui peut ouvrir ce fichier de solution.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Définitions

`Microsoft Visual Studio Solution File, Format Version 12.00`\
En-tête standard qui définit la version format de fichier.

`# Visual Studio Version 16`\
La version principale de Visual Studio qui (plus récemment) a enregistré ce fichier de solution. Ces informations contrôlent le numéro de version dans l’icône de la solution.

`VisualStudioVersion = 16.0.28701.123`\
La version complète de Visual Studio qui (plus récemment) a enregistré le fichier de solution. Si le fichier de solution est enregistré par une version plus récente de Visual Studio qui a la même version majeure, cette valeur n’est pas mise à jour afin de réduire le taux de désabonnement dans le fichier.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La version minimale (la plus ancienne) de Visual Studio qui peut ouvrir ce fichier de solution.

::: moniker-end

## <a name="file-body"></a>Corps de fichier

Le corps d’un fichier .sln se `GlobalSection`compose de plusieurs sections étiquetées, comme ceci:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Pour charger une solution, l’environnement effectue la séquence suivante de tâches :

1. L’environnement lit la section globale du fichier .sln et traite toutes les sections marquées `preSolution`. Dans ce fichier d’exemple, il y a une telle déclaration :

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Lorsque l’environnement `GlobalSection('name')` lit l’étiquette, il cartographie le nom à un VSPackage en utilisant le registre. Le nom clé devrait exister dans le\\ registre en vertu [HKLM<application ID Registry Root\>'SolutionPersistence’AggregateGUIDs]. La valeur par défaut des clés est le package GUID (REG_SZ) du VSPackage qui a écrit les entrées.

2. L’environnement charge le VSPackage, fait appel `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> à la VSPackage pour l’interface, et appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> méthode avec les données dans la section afin que le VSPackage peut stocker les données. L’environnement répète ce `preSolution` processus pour chaque section.

3. L’environnement s’étend à travers les blocs de persistance du projet. Dans ce cas, il y a un projet.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Cette déclaration contient le projet unique GUID et le type de projet GUID. Ces informations sont utilisées par l’environnement pour trouver le fichier de projet ou les fichiers appartenant à la solution, et le VSPackage requis pour chaque projet. Le projet GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> est passé pour charger le VSPackage spécifique lié au projet, puis le projet est chargé par le VSPackage. Dans ce cas, le VSPackage qui est chargé pour ce projet est Visual Basic.

   Chaque projet peut persister une id d’instance de projet unique afin qu’il puisse être consulté au besoin par d’autres projets dans la solution. Idéalement, si la solution et les projets sont sous contrôle de code source, le chemin vers le projet doit être relatif à la voie de la solution. Lorsque la solution est chargée pour la première fois, les fichiers du projet ne peuvent pas être sur la machine de l’utilisateur. En faisant stocker le fichier de projet sur le serveur par rapport au fichier de solution, il est relativement simple de trouver et de copier le fichier du projet à la machine de l’utilisateur. Il copie ensuite et charge le reste des fichiers nécessaires pour le projet.

4. D’après les informations contenues dans la section projet du fichier .sln, l’environnement charge chaque fichier de projet. Le projet lui-même est alors chargé de remplir la hiérarchie du projet et de charger tous les projets imbriqués.

5. Une fois que toutes les sections du fichier .sln sont traitées, la solution est affichée dans Solution Explorer et est prête à être modifiée par l’utilisateur.

Si un VSPackage qui implémente un projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> dans la solution ne se charge pas, la méthode est appelée et tous les autres projets de la solution ont la possibilité d’ignorer les changements qu’il aurait pu apporter lors du chargement. Si des erreurs d’analyse se produisent, autant d’informations que possible est conservée avec les fichiers de solution et l’environnement affiche une boîte de dialogue avertissant l’utilisateur que la solution est corrompue.

Lorsque la solution est sauvegardée ou fermée, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> méthode est appelée et transmise à la hiérarchie pour voir si des modifications ont été apportées à la solution qui doit être saisie dans le fichier .sln. Une valeur nulle, `QuerySaveSolutionProps` transmise <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>à l’in , indique que l’information est persistée pour la solution. Si la valeur n’est pas nulle, l’information persistante est <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> pour un projet spécifique, déterminé par le pointeur à l’interface.

S’il y a des <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> informations à lire, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> l’interface est appelée avec un pointeur de la méthode. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> méthode est ensuite appelée par l’environnement `IPropertyBag` pour récupérer les paires de nom-valeur de l’interface et écrire les informations sur le fichier .sln.

`SaveSolutionProps`et `WriteSolutionProps` les objets sont appelés de façon récursive `IPropertyBag` par l’environnement pour récupérer les informations à économiser de l’interface jusqu’à ce que tous les changements ont été entrés dans le fichier .sln. De cette façon, vous pouvez vous assurer que l’information sera persistée avec la solution et disponible la prochaine fois que la solution est ouverte.

Chaque VSPackage chargé est énuméré pour voir s’il a quelque chose à enregistrer pour .sln fichier. Ce n’est qu’au moment de la charge que les clés du registre sont interrogées. L’environnement connaît tous les paquets chargés parce qu’ils sont en mémoire au moment où la solution est sauvegardée.

Seul le fichier .sln `preSolution` contient `postSolution` des entrées dans les sections et. Il n’y a pas de sections similaires dans le fichier .suo puisque la solution a besoin de cette information pour charger correctement. Le fichier .suo contient des options spécifiques à l’utilisateur, telles que des notes privées, qui ne sont pas destinées à être partagées ou placées sous contrôle de code source.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Fichiers des options utilisateur de solution (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Solutions](../../extensibility/internals/solutions-overview.md)
