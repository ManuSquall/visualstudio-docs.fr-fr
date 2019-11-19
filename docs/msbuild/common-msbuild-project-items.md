---
title: Éléments communs des projets MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb759ba9571e16d0030f1fd6baf6d4feb03efb2e
ms.sourcegitcommit: 510529f2f86a9897ed5767973e60c99c0d3a77a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73956145"
---
# <a name="common-msbuild-project-items"></a>Éléments communs des projets MSBuild
Dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], un élément est une référence nommée à un ou plusieurs fichiers. Les éléments contiennent des métadonnées, comme des noms de fichiers, des chemins et des numéros de version. Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tous les types de projets ont plusieurs éléments en commun. Ces éléments sont définis dans le fichier *Microsoft.Build.CommonTypes.xsd*.

## <a name="common-items"></a>Éléments communs
 Voici une liste de tous les éléments de projet communs.

### <a name="reference"></a>Reference
 Représente une référence (managée) d'assembly dans le projet.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|HintPath|Chaîne facultative. Chemin d'accès relatif ou absolu de l'assembly.|
|Name|Chaîne facultative. Nom complet de l'assembly, par exemple, « System.Windows.Forms ».|
|FusionName|Chaîne facultative. Spécifie le nom de fusion simple ou fort de l'élément.<br /><br /> La présence de cet attribut peut faire gagner du temps, car il vous évite d'ouvrir le fichier d'assembly pour obtenir le nom de fusion.|
|SpecificVersion|Valeur booléenne facultative. Indique si seule la version figurant dans le nom de fusion doit être référencée.|
|Alias|Chaîne facultative. Alias éventuels de la référence.|
|Private|Valeur booléenne facultative. Indique si la référence doit être copiée dans le dossier de sortie. Cet attribut correspond à la propriété **Copie locale** de la référence qui se trouve dans l’IDE Visual Studio.|

### <a name="comreference"></a>COMReference
 Représente une référence de composant (non managé) COM dans le projet. Cet élément s’applique uniquement aux projets .NET.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|Name|Chaîne facultative. Nom complet du composant.|
|GUID|Chaîne requise. GUID du composant sous la forme {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Chaîne requise. Partie principale du numéro de version du composant. Par exemple, « 5 » si le numéro de version complet est « 5.46 ».|
|VersionMinor|Chaîne requise. Partie secondaire du numéro de version du composant. Par exemple, « 46 » si le numéro de version complet est « 5.46 ».|
|dans le dossier HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\|Chaîne facultative. LocaleID du composant.|
|WrapperTool|Chaîne facultative. Nom de l'outil wrapper utilisé sur le composant, par exemple, « tlbimp ».|
|Isolated|Valeur booléenne facultative. Indique si le composant est un composant sans inscription.|

### <a name="comfilereference"></a>COMFileReference
 Représente une liste de bibliothèques de types qui sont passées au paramètre `TypeLibFiles` de la cible [ResolveComReference](resolvecomreference-task.md). Cet élément s’applique uniquement aux projets .NET.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|WrapperTool|Chaîne facultative. Nom de l'outil wrapper utilisé sur le composant, par exemple, « tlbimp ».|

### <a name="nativereference"></a>NativeReference
 Représente un fichier manifeste natif ou une référence à un fichier de ce type.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|Name|Chaîne requise. Nom de base du fichier manifeste.|
|HintPath|Chaîne requise. Chemin d'accès relatif du fichier manifeste.|

### <a name="projectreference"></a>ProjectReference
 Représente une référence à un autre projet.

|Nom des métadonnées de l’élément|Description|
|---------------|-----------------|
|Name|Chaîne facultative. Nom complet de la référence.|
|Projet|Chaîne facultative. GUID de la référence sous la forme {12345678-1234-1234-1234-1234567891234}.|
|Package|Chaîne facultative. Chemin d'accès du fichier projet référencé.|
|ReferenceOutputAssembly|Valeur booléenne facultative. Si sa valeur est `false`, n’inclut pas la sortie du projet référencé comme [Référence](#reference) de ce projet, mais fait quand même en sorte que l’autre projet se génère avant celui-ci. La valeur par défaut est `true`.|

### <a name="compile"></a>Compile
 Représente les fichiers sources du compilateur.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| AutoGen | Valeur booléenne facultative. Indique si le fichier a été généré pour le projet par l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Lien | Chaîne facultative. Chemin d’accès codifiable à afficher quand le fichier se trouve physiquement en dehors de l’influence du fichier projet. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs possibles sont :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource
 Représente les ressources à incorporer dans l'assembly généré.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| Générateur | Chaîne requise. Nom du générateur de fichier exécuté sur cet élément. |
| LastGenOutput | Chaîne requise. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément. |
| CustomToolNamespace | Chaîne requise. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code. |
| Lien | Chaîne facultative. Le chemin d’accès codifiable s’affiche si le fichier se trouve physiquement en dehors de l’influence du projet. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs possibles sont :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |
| LogicalName | Chaîne requise. Nom logique de la ressource incorporée. |

### <a name="content"></a>Contenu
 Représente les fichiers qui ne sont pas compilés dans le projet, mais qui peuvent être incorporés ou publiés en même temps.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| Générateur | Chaîne requise. Nom du générateur de fichier qui s'exécute sur cet élément. |
| LastGenOutput | Chaîne requise. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément. |
| CustomToolNamespace | Chaîne requise. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code. |
| Lien | Chaîne facultative. Chemin d'accès codifiable à afficher si le fichier se trouve physiquement en dehors de l'influence du projet. |
| PublishState | Chaîne requise. État de publication du contenu, à savoir :<br /><br /> -   Default<br />-   Included<br />-   Excluded<br />-   DataFile<br />-   Prerequisite |
| IsAssembly | Valeur booléenne facultative. Indique si le fichier est un assembly. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs possibles sont :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |

### <a name="none"></a>aucune.
 Représente les fichiers qui ne doivent avoir aucun rôle dans le processus de génération.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| DependentUpon | Chaîne facultative. Spécifie le fichier dont dépend ce fichier pour une compilation correcte. |
| Générateur | Chaîne requise. Nom du générateur de fichier exécuté sur cet élément. |
| LastGenOutput | Chaîne requise. Nom du fichier créé par le générateur de fichier qui a été exécuté sur cet élément. |
| CustomToolNamespace | Chaîne requise. Espace de noms dans lequel le générateur de fichier s'exécutant sur cet élément doit créer du code. |
| Lien | Chaîne facultative. Chemin d'accès codifiable à afficher si le fichier se trouve physiquement en dehors de l'influence du projet. |
| Visible | Valeur booléenne facultative. Indique si le fichier doit être affiché dans **l’Explorateur de solutions** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Chaîne facultative. Détermine si le fichier doit être copié dans le répertoire de sortie. Les valeurs possibles sont :<br /><br /> 1. jamais<br />2. toujours<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata
 Représente les attributs d’assembly à générer comme `[AssemblyMetadata(key, value)]`.

| Nom des métadonnées de l’élément | Description |
|-----------------------| - |
| Inclure | Devient le premier paramètre (la clé) dans le constructeur d’attribut `AssemblyMetadataAttribute`. |
| valeur | Chaîne requise. Devient le deuxième paramètre (la valeur) dans le constructeur d’attribut `AssemblyMetadataAttribute`. |

> [!NOTE]
> Cela s’applique uniquement aux projets qui utilisent l’kit SDK .NET Core.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest
 Représente le manifeste d'application de base de la build et contient les informations de sécurité de déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

### <a name="codeanalysisimport"></a>CodeAnalysisImport
 Représente le projet FxCop à importer.

### <a name="import"></a>Import
 Représente les assemblys dont les espaces de noms doivent être importés par le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Voir aussi
- [Propriétés communes des projets MSBuild](../msbuild/common-msbuild-project-properties.md)
