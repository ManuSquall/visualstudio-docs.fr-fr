---
title: Solution (. Sln)
description: En savoir plus sur le fichier. sln, qui est l’un des fichiers qui gère les informations d’état d’un projet dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27364382a7e4318fce822b148e9d3df6747bfd1e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081995"
---
# <a name="solution-sln-file"></a>Fichier solution (. sln)

Une solution est une structure d’organisation des projets dans Visual Studio. La solution conserve les informations d’état des projets dans deux fichiers :

- fichier. sln (texte, partagé)

- fichier. suo (options de solution binaires, spécifiques à l’utilisateur)

Pour plus d’informations sur les fichiers. suo, consultez [options de l’utilisateur de la solution (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Si votre VSPackage est chargé à la suite d’un référencement dans le fichier. sln, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> pour lire dans le fichier. sln.

Le fichier. sln contient des informations textuelles que l’environnement utilise pour rechercher et charger les paramètres nom-valeur pour les données persistantes et les VSPackages de projet qu’il référence. Lorsqu’un utilisateur ouvre une solution, l’environnement parcourt `preSolution` les `Project` informations, et du `postSolution` fichier. sln pour charger la solution, les projets de la solution et toutes les informations persistantes attachées à la solution.

Chaque fichier de projet contient des informations supplémentaires lues par l’environnement pour remplir la hiérarchie avec les éléments de ce projet. La persistance des données de hiérarchie est contrôlée par le projet. Les données ne sont normalement pas stockées dans le fichier. sln, bien que vous puissiez écrire intentionnellement des informations de projet dans le fichier. sln si vous choisissez de le faire. Pour plus d’informations sur la persistance, consultez [persistance de projet](../../extensibility/internals/project-persistence.md) et [ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>En-tête de fichier

L’en-tête d’un fichier. sln ressemble à ceci :

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Définitions

`Microsoft Visual Studio Solution File, Format Version 12.00`\
En-tête standard qui définit la version du format de fichier.

`# Visual Studio 15`\
Version principale de Visual Studio qui a enregistré ce fichier de solution (le plus récemment). Ces informations contrôlent le numéro de version dans l’icône de la solution.

`VisualStudioVersion = 15.0.26730.15`\
Version complète de Visual Studio qui a enregistré le fichier de solution (le plus récemment). Si le fichier solution est enregistré par une version plus récente de Visual Studio qui a la même version majeure, cette valeur n’est pas mise à jour pour réduire l’évolution dans les fichiers solution.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Version minimale (la plus ancienne) de Visual Studio qui peut ouvrir ce fichier solution.

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
En-tête standard qui définit la version du format de fichier.

`# Visual Studio Version 16`\
Version principale de Visual Studio qui a enregistré ce fichier de solution (le plus récemment). Ces informations contrôlent le numéro de version dans l’icône de la solution.

`VisualStudioVersion = 16.0.28701.123`\
Version complète de Visual Studio qui a enregistré le fichier de solution (le plus récemment). Si le fichier solution est enregistré par une version plus récente de Visual Studio qui a la même version majeure, cette valeur n’est pas mise à jour pour réduire l’évolution dans le fichier.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Version minimale (la plus ancienne) de Visual Studio qui peut ouvrir ce fichier solution.

::: moniker-end

## <a name="file-body"></a>Corps du fichier

Le corps d’un fichier. sln est constitué de plusieurs sections étiquetées `GlobalSection` , comme suit :

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

Pour charger une solution, l’environnement effectue la séquence de tâches suivante :

1. L’environnement lit la section globale du fichier. sln et traite toutes les sections marquées `preSolution` . Dans cet exemple de fichier, il existe une telle instruction :

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Lorsque l’environnement lit la `GlobalSection('name')` balise, il mappe le nom à un VSPackage à l’aide du Registre. Le nom de clé doit exister dans le Registre sous [HKLM \\<racine du registre de l’ID d’application \> \SolutionPersistence\AggregateGUIDs]. La valeur par défaut des clés est le GUID du package (REG_SZ) du VSPackage qui a écrit les entrées.

2. L’environnement charge le VSPackage, appelle `QueryInterface` sur le VSPackage pour l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface et appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> méthode avec les données de la section afin que le VSPackage puisse stocker les données. L’environnement répète ce processus pour chaque `preSolution` section.

3. L’environnement itère au sein des blocs de persistance du projet. Dans ce cas, il existe un projet.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Cette instruction contient le GUID du projet unique et le GUID du type de projet. Ces informations sont utilisées par l’environnement pour rechercher le fichier projet ou les fichiers appartenant à la solution, ainsi que le VSPackage requis pour chaque projet. Le GUID du projet est passé à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> pour charger le VSPackage spécifique lié au projet, puis le projet est chargé par le VSPackage. Dans ce cas, le VSPackage qui est chargé pour ce projet est Visual Basic.

   Chaque projet peut conserver un ID d’instance de projet unique afin qu’il soit accessible en fonction des besoins d’autres projets de la solution. Dans l’idéal, si la solution et les projets sont sous contrôle de code source, le chemin d’accès au projet doit être relatif au chemin d’accès à la solution. Lorsque la solution est chargée pour la première fois, les fichiers projet ne peuvent pas se trouver sur l’ordinateur de l’utilisateur. En faisant en sorte que le fichier projet soit stocké sur le serveur par rapport au fichier solution, il est relativement simple de trouver et de copier le fichier projet sur l’ordinateur de l’utilisateur. Il copie et charge ensuite le reste des fichiers nécessaires pour le projet.

4. En fonction des informations contenues dans la section projet du fichier. sln, l’environnement charge chaque fichier projet. Le projet lui-même est ensuite chargé de remplir la hiérarchie du projet et de charger tous les projets imbriqués.

5. Une fois toutes les sections du fichier. sln traitées, la solution s’affiche dans Explorateur de solutions et est prête à être modifiée par l’utilisateur.

Si un VSPackage qui implémente un projet dans la solution ne parvient pas à se charger, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> méthode est appelée et chaque autre projet de la solution a la possibilité d’ignorer les modifications qu’il a pu effectuer pendant le chargement. Si des erreurs d’analyse se produisent, le plus grand nombre d’informations possible est préservé avec les fichiers de la solution et l’environnement affiche une boîte de dialogue qui avertit l’utilisateur que la solution est endommagée.

Lorsque la solution est enregistrée ou fermée, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> méthode est appelée et transmise à la hiérarchie pour voir si des modifications ont été apportées à la solution qui doivent être entrées dans le fichier. sln. Une valeur null, passée à `QuerySaveSolutionProps` dans <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , indique que les informations sont conservées pour la solution. Si la valeur n’est pas null, les informations persistantes sont pour un projet spécifique, déterminé par le pointeur vers l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface.

S’il y a des informations à enregistrer, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface est appelée avec un pointeur vers la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> méthode. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> méthode est ensuite appelée par l’environnement pour récupérer les paires nom-valeur de l' `IPropertyBag` interface et écrire les informations dans le fichier. sln.

`SaveSolutionProps``WriteSolutionProps`les objets et sont appelés de manière récursive par l’environnement pour récupérer les informations à enregistrer à partir de l' `IPropertyBag` interface jusqu’à ce que toutes les modifications aient été entrées dans le fichier. sln. De cette façon, vous pouvez vous assurer que les informations sont conservées avec la solution et disponibles la prochaine fois que la solution est ouverte.

Chaque VSPackage chargé est énuméré pour voir s’il a quelque chose à enregistrer dans le fichier. sln. Elle est uniquement au moment du chargement où les clés de Registre sont interrogées. L’environnement connaît tous les packages chargés, car ils sont en mémoire au moment où la solution est enregistrée.

Seul le fichier. sln contient des entrées dans `preSolution` les `postSolution` sections et. Il n’existe pas de sections similaires dans le fichier. suo puisque la solution a besoin de ces informations pour se charger correctement. Le fichier. suo contient des options spécifiques à l’utilisateur, telles que des notes privées, qui ne sont pas destinées à être partagées ou placées sous le contrôle de code source.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Fichiers des options utilisateur de solution (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Solutions](../../extensibility/internals/solutions-overview.md)
