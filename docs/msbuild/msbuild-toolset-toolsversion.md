---
title: "Ensemble d’outils MSBuild (ToolsVersion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 6a45db14ee055c4fbdf738cf36df503a4a1fffd0
ms.contentlocale: fr-fr
ms.lasthandoff: 05/31/2017

---
# <a name="msbuild-toolset-toolsversion"></a>Ensemble d'outils MSBuild (ToolsVersion)
MSBuild utilise un ensemble d’outils de tâches, de cibles et d’outils pour générer une application. Un ensemble d'outils MSBuild comprend généralement un fichier microsoft.common.tasks, un fichier microsoft.common.targets et des compilateurs comme csc.exe et vbc.exe. La plupart des ensembles d'outils peuvent être utilisés pour compiler des applications pour plusieurs versions de .NET Framework et pour plusieurs plateformes système. Cependant, l'ensemble d'outils MSBuild 2.0 ne peut être utilisé que pour cibler .NET Framework 2.0.  
  
## <a name="toolsversion-attribute"></a>Attribut ToolsVersion  
 Spécifiez l’ensemble d’outils dans l’attribut `ToolsVersion` de l’élément [Project](../msbuild/project-element-msbuild.md) du fichier projet. L'exemple suivant spécifie que le projet doit être généré en utilisant l'ensemble d'outils MSBuild 12.0.  
  
```xml  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## <a name="how-the-toolsversion-attribute-works"></a>Fonctionnement de l'attribut ToolsVersion  
 Quand vous créez un projet dans Visual Studio ou que vous mettez à niveau un projet existant, un attribut nommé `ToolsVersion` est automatiquement inclus dans le fichier projet, et sa valeur correspond à la version de MSBuild incluse dans l’édition de Visual Studio. Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Quand une valeur pour `ToolsVersion` est définie dans un fichier projet, MSBuild utilise cette valeur pour déterminer les valeurs des propriétés de l'ensemble d'outils qui sont disponibles pour le projet. Une des propriétés de l'ensemble d'outils est `$(MSBuildToolsPath)`, qui spécifie le chemin d'accès aux outils .NET Framework. Cette propriété de l'ensemble d'outils (ou `$(MSBuildBinPath)`) est la seule propriété obligatoire.  
  
 Depuis Visual Studio 2013, la version de l'ensemble d'outils MSBuild est identique au numéro de version de Visual Studio. MSBuild utilise par défaut cet ensemble d'outils dans Visual Studio et sur la ligne de commande, quelle que soit la version de l'ensemble d'outils spécifiée dans le fichier projet.  Ce comportement peut être remplacé à l'aide de l'indicateur /ToolsVersion. Pour plus d’informations, consultez [Substitution des paramètres ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Dans l'exemple suivant, MSBuild trouve le fichier Microsoft.CSharp.targets en utilisant la propriété réservée `MSBuildToolsPath`.  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Vous pouvez modifier la valeur de `MSBuildToolsPath` en définissant un ensemble d'outils personnalisé. Pour plus d’informations, consultez [Configurations standard et personnalisée de l’ensemble d’outils](../msbuild/standard-and-custom-toolset-configurations.md).  
  
 Quand vous générez une solution sur la ligne de commande et que vous spécifiez `ToolsVersion` pour msbuild.exe, tous les projets et leurs dépendances de projet à projet sont créés conformément à `ToolsVersion`, même si chaque projet de la solution spécifie son propre attribut `ToolsVersion`. Pour définir la valeur `ToolsVersion` par projet, consultez [Substitution des paramètres ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 L'attribut `ToolsVersion` est également utilisé pour la migration de projet. Par exemple, si vous ouvrez un projet Visual Studio 2008 dans Visual Studio 2010, le fichier projet est mis à jour de façon à inclure ToolsVersion="4.0". Si vous essayez ensuite d’ouvrir ce projet dans Visual Studio 2008, il ne reconnaît pas l’attribut `ToolsVersion` mis à niveau et génère donc le projet comme si l’attribut avait toujours la valeur 3.5.  
  
 Visual Studio 2010 et Visual Studio 2012 utilisent la valeur 4.0 pour ToolsVersion. Visual Studio 2013 utilise la valeur 12.0 pour ToolsVersion. Visual Studio 2015 utilise ToolsVersion 14.0, tandis que Visual Studio 2017 utilise ToolsVersion 15.0. Dans de nombreux cas, vous pouvez ouvrir le projet dans plusieurs versions de Visual Studio sans rien modifier. Visual Studio utilise toujours l'ensemble d'outils correct, mais vous recevrez une notification si la version utilisée ne correspond pas à la version spécifiée dans le fichier projet. Dans la plupart des cas, cet avertissement est bénin, car les ensembles d'outils sont généralement compatibles.  
  
 Les sous-ensembles d'outils, qui sont décrits plus loin dans cette rubrique, permettent à MSBuild de passer automatiquement à l'ensemble d'outils à utiliser en fonction du contexte dans lequel la génération est effectuée. Par exemple, MSBuild utilise un ensemble d'outils plus récent quand il est exécuté dans Visual Studio 2012 que quand il est exécuté avec Visual Studio 2010, sans que vous ayez à changer explicitement le fichier projet.  
  
## <a name="toolset-implementation"></a>Implémentation d'un ensemble d'outils  
 Implémentez un ensemble d'outils en sélectionnant les chemins d'accès aux différents outils, cibles et tâches qui constituent l'ensemble d'outils. Les outils de l'ensemble d'outils défini par MSBuild proviennent des sources suivantes :  
  
-   Le dossier .NET Framework  
  
-   Des outils managés supplémentaires  
  
 Les outils managés comprennent ResGen.exe et TlbImp.exe.  
  
 MSBuild offre deux façons d'accéder à l'ensemble d'outils :  
  
-   À l'aide des propriétés de l'ensemble d'outils  
  
-   À l'aide des méthodes de <xref:Microsoft.Build.Utilities.ToolLocationHelper>  
  
 Les propriétés de l'ensemble d'outils spécifient les chemins d'accès aux outils. MSBuild utilise la valeur de l'attribut `ToolsVersion` dans le fichier projet pour trouver la clé de Registre correspondante, puis utilise les informations de cette clé pour définir les propriétés de l'ensemble d'outils. Par exemple, si `ToolsVersion` a la valeur `12.0`, MSBuild définit les propriétés de l’ensemble d’outils en fonction de cette clé de Registre : HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.  
  
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
 Comme décrit plus haut dans cette rubrique, MSBuild utilise une clé de Registre pour spécifier le chemin d'accès des outils de base. Si la clé a une sous-clé, MSBuild l'utilise pour spécifier le chemin d'accès d'un sous-ensemble d'outils qui contient des outils supplémentaires. Dans ce cas, l'ensemble d'outils est défini en combinant les définitions des propriétés qui sont définies dans les deux clés.  
  
> [!NOTE]
>  Si les noms des propriétés de l'ensemble d'outils sont en conflit, la valeur qui est définie pour la sous-clé remplace la valeur définie pour le chemin d'accès de la clé racine.  
  
 Les sous-ensembles d'outils deviennent actifs en présence de la propriété de build `VisualStudioVersion`. Cette propriété peut prendre une de ces valeurs :  
  
-   "10.0" spécifie le sous-ensemble d’outils du .NET Framework 4  
  
-   "11.0" spécifie le sous-ensemble d’outils du .NET Framework 4.5  
  
-   "12.0" spécifie le sous-ensemble d’outils du .NET Framework 4.5.1  
  
 Les sous-ensembles d'outils 10.0 et 11.0 doivent être utilisés avec la valeur 4.0 pour ToolsVersion. Dans les versions ultérieures, la version du sous-ensemble d'outils et la valeur de ToolsVersion doivent correspondre.  
  
 Lors d'une génération, MSBuild détermine et définit automatiquement une valeur par défaut pour la propriété `VisualStudioVersion` si elle n'est pas déjà définie.  
  
 MSBuild fournit des surcharges pour les méthodes `ToolLocationHelper`, qui ajoutent une valeur énumérée de `VisualStudioVersion` comme paramètre.  
  
 Les sous-ensembles d'outils ont été introduits dans .NET Framework 4.5.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurations standard et personnalisée de l’ensemble d’outils](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Multiciblage](../msbuild/msbuild-multitargeting-overview.md)

