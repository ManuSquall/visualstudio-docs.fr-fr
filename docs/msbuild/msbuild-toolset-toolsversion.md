---
title: Ensemble d’outils MSBuild (ToolsVersion) | Microsoft Docs
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2684ed1389556dfb96bf8eeb113f82336eb8c6d0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605183"
---
# <a name="msbuild-toolset-toolsversion"></a>Ensemble d'outils MSBuild (ToolsVersion)
MSBuild utilise un ensemble d’outils de tâches, de cibles et d’outils pour générer une application. Un ensemble d’outils MSBuild comprend généralement un fichier *microsoft.common.tasks*, un fichier *microsoft.common.targets* et des compilateurs comme *csc.exe* et *vbc.exe*. La plupart des ensembles d'outils peuvent être utilisés pour compiler des applications pour plusieurs versions de .NET Framework et pour plusieurs plateformes système. Cependant, l'ensemble d'outils MSBuild 2.0 ne peut être utilisé que pour cibler .NET Framework 2.0.

## <a name="toolsversion-attribute"></a>Attribut ToolsVersion
 Spécifiez l’ensemble d’outils dans l’attribut `ToolsVersion` de l’élément [Project](../msbuild/project-element-msbuild.md) du fichier projet. L’exemple suivant spécifie que le projet doit être généré à l’aide de l’ensemble d’outils MSBuild 15.0.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

> [!NOTE]
> Certains types de projets utilisent l’attribut `sdk` à la place de `ToolsVersion`. Pour plus d’informations, voir [Packages, métadonnées et frameworks](/dotnet/core/packages) et [Ajouts au format csproj pour .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Fonctionnement de l’attribut ToolsVersion
 Quand vous créez un projet dans Visual Studio ou que vous mettez à niveau un projet existant, un attribut nommé `ToolsVersion` est automatiquement inclus dans le fichier projet, et sa valeur correspond à la version de MSBuild incluse dans l’édition de Visual Studio. Pour plus d’informations, voir [Cibler une version spécifique de .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

 Quand une valeur pour `ToolsVersion` est définie dans un fichier projet, MSBuild utilise cette valeur pour déterminer les valeurs des propriétés de l'ensemble d'outils qui sont disponibles pour le projet. Une des propriétés de l'ensemble d'outils est `$(MSBuildToolsPath)`, qui spécifie le chemin d'accès aux outils .NET Framework. Cette propriété de l'ensemble d'outils (ou `$(MSBuildBinPath)`) est la seule propriété obligatoire.

 Depuis Visual Studio 2013, la version de l'ensemble d'outils MSBuild est identique au numéro de version de Visual Studio. MSBuild utilise par défaut cet ensemble d’outils dans Visual Studio et en ligne de commande, quelle que soit la version de l’ensemble d’outils spécifiée dans le fichier projet.  Ce comportement peut être remplacé à l’aide de l’indicateur -ToolsVersion. Pour plus d’informations, voir [Écraser les paramètres ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 Dans l’exemple suivant, MSBuild trouve le fichier *Microsoft.CSharp.targets* en utilisant la propriété réservée `MSBuildToolsPath`.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Vous pouvez modifier la valeur de `MSBuildToolsPath` en définissant un ensemble d'outils personnalisé. Pour plus d’informations, voir [Configurations standard et personnalisées des ensembles d’outils](../msbuild/standard-and-custom-toolset-configurations.md).

 Quand vous générez une solution en ligne de commande et que vous spécifiez `ToolsVersion` pour *msbuild.exe*, tous les projets et leurs dépendances de projet à projet sont créés conformément à `ToolsVersion`, même si chacun des projets de la solution spécifie son propre paramètre `ToolsVersion`. Pour définir la valeur `ToolsVersion` projet par projet, voir [Écraser les paramètres ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 L'attribut `ToolsVersion` est également utilisé pour la migration de projet. Par exemple, si vous ouvrez un projet Visual Studio 2008 dans Visual Studio 2010, le fichier projet est mis à jour de façon à inclure ToolsVersion="4.0". Si vous essayez ensuite d’ouvrir ce projet dans Visual Studio 2008, il ne reconnaît pas l’attribut `ToolsVersion` mis à niveau et génère donc le projet comme si l’attribut avait toujours la valeur 3.5.

 Visual Studio 2010 et Visual Studio 2012 utilisent la valeur 4.0 pour ToolsVersion. Visual Studio 2013 utilise la valeur 12.0 pour ToolsVersion. Visual Studio 2015 utilise ToolsVersion 14.0, tandis que Visual Studio 2017 utilise ToolsVersion 15.0. Dans de nombreux cas, vous pouvez ouvrir le projet dans plusieurs versions de Visual Studio sans rien modifier. Visual Studio utilise toujours l'ensemble d'outils correct, mais vous recevrez une notification si la version utilisée ne correspond pas à la version spécifiée dans le fichier projet. Dans la plupart des cas, cet avertissement est bénin, car les ensembles d'outils sont généralement compatibles.

 Les sous-ensembles d'outils, qui sont décrits plus loin dans cette rubrique, permettent à MSBuild de passer automatiquement à l'ensemble d'outils à utiliser en fonction du contexte dans lequel la génération est effectuée. Par exemple, MSBuild utilise un ensemble d'outils plus récent quand il est exécuté dans Visual Studio 2012 que quand il est exécuté avec Visual Studio 2010, sans que vous ayez à changer explicitement le fichier projet.

## <a name="toolset-implementation"></a>Implémentation d’un ensemble d’outils
 Implémentez un ensemble d'outils en sélectionnant les chemins d'accès aux différents outils, cibles et tâches qui constituent l'ensemble d'outils. Les outils de l'ensemble d'outils défini par MSBuild proviennent des sources suivantes :

- Le dossier .NET Framework

- Des outils managés supplémentaires

  Parmi les outils managés figurent *ResGen.exe* et *TlbImp.exe*.

MSBuild offre deux façons d'accéder à l'ensemble d'outils :

-   À l'aide des propriétés de l'ensemble d'outils

-   À l'aide des méthodes de <xref:Microsoft.Build.Utilities.ToolLocationHelper>

Les propriétés de l'ensemble d'outils spécifient les chemins d'accès aux outils. À compter de Visual Studio 2017, MSBuild n’a plus d’emplacement fixe. Par défaut, il se trouve dans le dossier *MSBuild\15.0\Bin* relatif à l’emplacement d’installation de Visual Studio. Dans les versions antérieures, MSBuild utilise la valeur de l’attribut `ToolsVersion` dans le fichier projet pour trouver la clé de Registre correspondante, puis utilise les informations de cette clé pour définir les propriétés de l’ensemble d’outils. Par exemple, si `ToolsVersion` a la valeur `12.0`, MSBuild définit les propriétés de l’ensemble d’outils en fonction de cette clé de Registre : **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Voici des propriétés de l'ensemble d'outils :

-   `MSBuildToolsPath` spécifie le chemin d'accès des fichiers binaires de MSBuild.

-   `SDK40ToolsPath` spécifie le chemin d'accès des outils managés supplémentaires pour MSBuild 4.x (qui peut être 4.0 ou 4.5).

-   `SDK35ToolsPath` spécifie le chemin d'accès des outils managés supplémentaires pour MSBuild 3.5.

Vous pouvez aussi déterminer l'ensemble d'outils par programmation en appelant les méthodes de la classe <xref:Microsoft.Build.Utilities.ToolLocationHelper>. La classe comprend ces méthodes :

-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> retourne le chemin d'accès du dossier .NET Framework.

-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> retourne le chemin d'accès d'un fichier du dossier .NET Framework.

-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> retourne le chemin d'accès du dossier des outils managés.

-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> retourne le chemin d'accès à un fichier qui se trouve généralement dans le dossier des outils managés.

-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> retourne le chemin d'accès des outils de génération.

### <a name="sub-toolsets"></a>Sous-ensembles d'outils
 Dans les versions de MSBuild antérieures à 15.0, MSBuild utilise une clé de Registre pour spécifier le chemin d’accès des outils de base. Si la clé a une sous-clé, MSBuild l'utilise pour spécifier le chemin d'accès d'un sous-ensemble d'outils qui contient des outils supplémentaires. Dans ce cas, l'ensemble d'outils est défini en combinant les définitions des propriétés qui sont définies dans les deux clés.

> [!NOTE]
>  Si les noms de propriétés de l’ensemble d’outils sont en conflit, la valeur définie pour le chemin d’accès de la sous-clé remplace celle du chemin d’accès de la clé racine.

 Les sous-ensembles d'outils deviennent actifs en présence de la propriété de build `VisualStudioVersion`. Cette propriété peut prendre une de ces valeurs :

-   "10.0" spécifie le sous-ensemble d’outils du .NET Framework 4

-   "11.0" spécifie le sous-ensemble d’outils du .NET Framework 4.5

-   "12.0" spécifie le sous-ensemble d’outils du .NET Framework 4.5.1

Les sous-ensembles d'outils 10.0 et 11.0 doivent être utilisés avec la valeur 4.0 pour ToolsVersion. Dans les versions ultérieures, la version du sous-ensemble d'outils et la valeur de ToolsVersion doivent correspondre.

Lors d'une génération, MSBuild détermine et définit automatiquement une valeur par défaut pour la propriété `VisualStudioVersion` si elle n'est pas déjà définie.

MSBuild fournit des surcharges pour les méthodes `ToolLocationHelper`, qui ajoutent une valeur énumérée de `VisualStudioVersion` comme paramètre.

Les sous-ensembles d'outils ont été introduits dans .NET Framework 4.5.

## <a name="see-also"></a>Voir aussi
- [Configurations standard et personnalisées des ensembles d’outils](../msbuild/standard-and-custom-toolset-configurations.md)
- [Multiciblage](../msbuild/msbuild-multitargeting-overview.md)
