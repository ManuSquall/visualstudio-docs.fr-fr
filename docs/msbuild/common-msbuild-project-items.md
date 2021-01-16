---
title: Éléments communs des projets MSBuild | Microsoft Docs
description: En savoir plus sur les éléments de projet MSBuild courants. Les éléments sont des références nommées à un ou plusieurs fichiers et ont des métadonnées telles que des noms de fichiers, des chemins d’accès et des numéros de version.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea072cf3e9a236fdc6a4ad66b1c0cf7ddcda1550
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533443"
---
# <a name="common-msbuild-project-items"></a>Éléments communs des projets MSBuild

Dans MSBuild, un élément est une référence nommée à un ou plusieurs fichiers. Les éléments contiennent des métadonnées, comme des noms de fichiers, des chemins et des numéros de version. Tous les types de projets dans Visual Studio ont plusieurs éléments en commun. Ces éléments sont définis dans le fichier *Microsoft.Build.CommonTypes.xsd*.

## <a name="common-items"></a>Éléments communs

Voici une liste de tous les éléments de projet communs.

### <a name="reference"></a>Informations de référence

Représente une référence (managée) d'assembly dans le projet.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|HintPath|Chaîne facultative. Chemin d'accès relatif ou absolu de l'assembly.|
|Nom|Chaîne facultative. Nom complet de l'assembly, par exemple, « System.Windows.Forms ».|
|FusionName|Chaîne facultative. Spécifie le nom de fusion simple ou fort de l'élément.<br /><br /> La présence de cet attribut peut faire gagner du temps, car il vous évite d'ouvrir le fichier d'assembly pour obtenir le nom de fusion.|
|SpecificVersion|Valeur booléenne facultative. Indique si seule la version figurant dans le nom de fusion doit être référencée.|
|Alias|Chaîne facultative. Alias éventuels de la référence.|
|Privé|Valeur booléenne facultative. Indique si la référence doit être copiée dans le dossier de sortie. Cet attribut correspond à la propriété **Copie locale** de la référence qui se trouve dans l’IDE Visual Studio.|

### <a name="comreference"></a>COMReference

Représente une référence de composant (non managé) COM dans le projet. Cet élément s’applique uniquement aux projets .NET.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|Nom|Chaîne facultative. Nom complet du composant.|
|Guid|Chaîne obligatoire. GUID du composant sous la forme {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Chaîne obligatoire. Partie principale du numéro de version du composant. Par exemple, « 5 » si le numéro de version complet est « 5.46 ».|
|VersionMinor|Chaîne obligatoire. Partie secondaire du numéro de version du composant. Par exemple, « 46 » si le numéro de version complet est « 5.46 ».|
|LCID|Chaîne facultative. LocaleID du composant.|
|WrapperTool|Chaîne facultative. Nom de l'outil wrapper utilisé sur le composant, par exemple, « tlbimp ».|
|Isolé|Valeur booléenne facultative. Indique si le composant est un composant sans inscription.|

### <a name="comfilereference"></a>COMFileReference

Représente une liste de bibliothèques de types qui sont passées au paramètre `TypeLibFiles` de la cible [ResolveComReference](resolvecomreference-task.md). Cet élément s’applique uniquement aux projets .NET.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|WrapperTool|Chaîne facultative. Nom de l'outil wrapper utilisé sur le composant, par exemple, « tlbimp ».|

### <a name="nativereference"></a>NativeReference

Représente un fichier manifeste natif ou une référence à un fichier de ce type.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|Nom|Chaîne obligatoire. Nom de base du fichier manifeste.|
|HintPath|Chaîne obligatoire. Chemin d'accès relatif du fichier manifeste.|

### <a name="projectreference"></a>ProjectReference

Représente une référence à un autre projet. `ProjectReference` les éléments sont transformés en éléments de [référence](#reference) par la `ResolveProjectReferences` cible, donc toutes les métadonnées valides sur une référence peuvent être valides sur `ProjectReference` , si le processus de transformation ne le remplace pas.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|Nom|Chaîne facultative. Nom complet de la référence.|
|GlobalPropertiesToRemove|`string[]` optionnel. Noms des propriétés à supprimer lors de la génération du projet référencé, par exemple `RuntimeIdentifier;PackOnBuild` . Vide par défaut.|
|Project|Chaîne facultative. GUID de la référence sous la forme {12345678-1234-1234-1234-1234567891234}.|
|OutputItemType|Chaîne facultative. Type d’élément dans lequel émettre des sorties cibles. La valeur par défaut est vide. Si les métadonnées de référence ont la valeur « true » (valeur par défaut), les sorties cibles deviennent des références pour le compilateur.|
|ReferenceOutputAssembly|Valeur booléenne facultative. Si sa valeur est `false`, n’inclut pas la sortie du projet référencé comme [Référence](#reference) de ce projet, mais fait quand même en sorte que l’autre projet se génère avant celui-ci. La valeur par défaut est `true`.|
|SetConfiguration|Chaîne facultative. Définit la propriété globale `Configuration` pour le projet référencé, par exemple `Configuration=Release` .|
|SetPlatform|Chaîne facultative. Définit la propriété globale `Platform` pour le projet référencé, par exemple `Platform=AnyCPU` .|
|SetTargetFramework|Chaîne facultative. Définit la propriété globale `TargetFramework` pour le projet référencé, par exemple `TargetFramework=netstandard2.0` .|
|SkipGetTargetFrameworkProperties|Valeur booléenne facultative. Si `true` , génère le projet référencé sans négocier la valeur la plus compatible `TargetFramework` . La valeur par défaut est `false`.|
|Cibles|`string[]` optionnel. Liste de cibles séparées par des points-virgules dans les projets référencés qui doivent être générés. La valeur par défaut est la valeur `$(ProjectReferenceBuildTargets)` qui est vide par défaut, ce qui indique les cibles par défaut.|

### <a name="compile"></a>Compiler

Représente les fichiers sources du compilateur.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| AutoGen | Valeur booléenne facultative. Indique si le fichier a été généré pour le projet par l’environnement de développement intégré (IDE) de Visual Studio. |
| Lien | Chaîne facultative. Chemin d’accès codifiable à afficher quand le fichier se trouve physiquement en dehors de l’influence du fichier projet. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **Explorateur de solutions** dans Visual Studio. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource

Représente les ressources à incorporer dans l'assembly généré.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| Générateur | Chaîne obligatoire. Nom du générateur de fichier exécuté sur cet élément. |
| LastGenOutput | Chaîne obligatoire. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément. |
| CustomToolNamespace | Chaîne obligatoire. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code. |
| Lien | Chaîne facultative. Le chemin d’accès codifiable s’affiche si le fichier se trouve physiquement en dehors de l’influence du projet. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **Explorateur de solutions** dans Visual Studio. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |
| LogicalName | Chaîne obligatoire. Nom logique de la ressource incorporée. |

### <a name="content"></a>Content

Représente les fichiers qui ne sont pas compilés dans le projet, mais qui peuvent être incorporés ou publiés en même temps.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| Générateur | Chaîne obligatoire. Nom du générateur de fichier qui s'exécute sur cet élément. |
| LastGenOutput | Chaîne obligatoire. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément. |
| CustomToolNamespace | Chaîne obligatoire. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code. |
| Lien | Chaîne facultative. Chemin d'accès codifiable à afficher si le fichier se trouve physiquement en dehors de l'influence du projet. |
| PublishState | Chaîne obligatoire. État de publication du contenu, à savoir :<br /><br /> -   Default<br />-   Included<br />-   Excluded<br />-   DataFile<br />-   Prerequisite |
| IsAssembly | Valeur booléenne facultative. Indique si le fichier est un assembly. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **Explorateur de solutions** dans Visual Studio. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |

### <a name="none"></a>None

Représente les fichiers qui ne doivent avoir aucun rôle dans le processus de génération.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| Générateur | Chaîne obligatoire. Nom du générateur de fichier exécuté sur cet élément. |
| LastGenOutput | Chaîne obligatoire. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément. |
| CustomToolNamespace | Chaîne obligatoire. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code. |
| Lien | Chaîne facultative. Chemin d'accès codifiable à afficher si le fichier se trouve physiquement en dehors de l'influence du projet. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **Explorateur de solutions** dans Visual Studio. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs sont les suivantes :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

Représente les attributs d’assembly à générer comme `[AssemblyMetadata(key, value)]` .

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| Inclure | Devient le premier paramètre (la clé) dans le `AssemblyMetadataAttribute` constructeur d’attribut. |
| Value | Chaîne obligatoire. Devient le deuxième paramètre (la valeur) dans le `AssemblyMetadataAttribute` constructeur d’attribut. |

> [!NOTE]
> Cet élément s’applique aux projets qui utilisent le kit de développement logiciel (SDK) pour .NET 5 (et .NET Core) et versions ultérieures.

### <a name="internalsvisibleto"></a>InternalsVisibleTo

Spécifie les assemblys à émettre en tant qu' `[InternalsVisibleTo(..)]` attributs d’assembly.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| Inclure | Nom de l'assembly. |
| Clé : | Chaîne facultative. Clé publique de l’assembly. |

> [!NOTE]
> Cet élément s’applique aux projets qui utilisent le kit de développement logiciel (SDK) pour .NET 5 (et .NET Core) et versions ultérieures.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Représente le manifeste d’application de base pour la génération et contient des informations de sécurité du déploiement ClickOnce.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

Représente le projet FxCop à importer.

### <a name="import"></a>Importer

Représente les assemblys dont les espaces de noms doivent être importés par le compilateur Visual Basic.

## <a name="see-also"></a>Voir aussi

- [Propriétés communes des projets MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Métadonnées communes d’éléments MSBuild](common-msbuild-item-metadata.md)