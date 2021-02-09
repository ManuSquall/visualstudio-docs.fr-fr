---
title: Détecter un problème et créer des journaux pour les problèmes MSBuild
description: Découvrez comment vous pouvez diagnostiquer les problèmes de build dans votre projet Visual Studio et, si nécessaire, créer un journal à envoyer à Microsoft pour investigation.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: d9308bff68a5a5377c025bba5861ac344dcb0326
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880487"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Détecter un problème et créer des journaux pour les problèmes MSBuild

Les procédures suivantes peuvent vous aider à diagnostiquer les problèmes de build dans votre projet Visual Studio et, si nécessaire, créer un journal à envoyer à Microsoft pour examen.

## <a name="a-property-value-is-ignored"></a>Une valeur de propriété est ignorée

Si une propriété de projet semble être définie sur une valeur particulière, mais n’a aucun effet sur la build, procédez comme suit :

1. Ouvrez l’invite de commandes développeur Studio Visual qui correspond à votre version de Visual Studio.
1. Exécutez la commande suivante, après avoir remplacé les valeurs pour votre chemin d’accès vers la solution, la configuration et le nom du projet :

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Cette commande génère un fichier de projet msbuild « prétraité » (out.xml). Vous pouvez rechercher une propriété spécifique de ce fichier afin de voir où elle est définie.

La dernière définition d’une propriété est ce que consomme la build. Si la propriété est définie à deux reprises, la deuxième valeur remplace la première. En outre, MSBuild évalue le projet dans plusieurs passes :

- PropertyGroup et importations
- ItemDefinitionGroups
- ItemGroup
- Targets

Par conséquent, étant donné l’ordre suivant :

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

La valeur de « MyMetadata » pour l’élément de « MyFile.txt » est évaluée sur « B » pendant la build (pas « A » et non vide)

## <a name="incremental-build-is-building-more-than-it-should"></a>La build incrémentielle génère plus qu’il le devrait

Si MSBuild régénère inutilement un projet ou élément de projet, créez un journal de génération détaillé ou binaire. Vous pouvez rechercher dans le journal le fichier qui a été généré ou compilé inutilement. La sortie ressemble à ceci :

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Si vous compilez dans l’IDE Visual Studio (avec commentaires relatifs à la Fenêtre Sortie détaillés), la **Fenêtre Sortie** affiche la raison pour laquelle chaque projet n'est pas à jour :

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Créer un journal binaire msbuild

1. Ouvrir l’invite de commandes développeur de votre version de Visual Studio
1. À partir de l’invite de commandes, exécutez les commandes suivantes. (N’oubliez pas d’utiliser vos valeurs de projet et de configuration réelles.) :

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    or

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Un fichier Msbuild.binlog sera créé dans le répertoire à partir duquel que vous avez exécuté MSBuild. Vous pouvez l’afficher et le rechercher à l’aide de la [Visionneuse du journal Msbuild structuré](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Créer un journal détaillé

1. Dans le menu principal de Visual Studio, accédez à **Outils**  >  **options**  >  **projets et solutions**  > **générer et exécuter**.
1. Définissez **Commentaires relatifs à la build du projet MSBuild** sur **Détaillé** dans les deux zones de liste déroulante. Les contrôles les plus hauts génèrent un niveau de détail dans le **fenêtre Sortie** et le deuxième contrôle génèrent des commentaires dans le \<projectname\> fichier. log créé dans le répertoire intermédiaire de chaque projet pendant la génération.
2. À partir d’une invite de commandes développeur Visual Studio, entrez une de ces commandes, en remplaçant les valeurs de chemin d’accès et de configuration courantes :

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    or

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Un fichier Msbuild.log sera créé dans le répertoire à partir duquel que vous avez exécuté msbuild.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
