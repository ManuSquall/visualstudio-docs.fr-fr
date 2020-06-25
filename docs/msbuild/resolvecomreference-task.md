---
title: ResolveCOMReference, tâche | Microsoft Docs
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b99e743cf5bc9e3e634a8738e30d17c8e5517191
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286178"
---
# <a name="resolvecomreference-task"></a>ResolveComReference, tâche

Prend une liste d’un ou plusieurs noms de bibliothèques de types ou de fichiers *.tlb* et résout ces bibliothèques de types aux emplacements sur le disque.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveCOMReference` .

|Paramètre|Description|
|---------------|-----------------|
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, place la clé publique dans l’assembly. Si la valeur est `false`, signe complètement l’assembly.|
|`EnvironmentVariables`|Paramètre `String[]` facultatif.<br /><br /> Tableau de paires de variables d'environnement, séparées par un signe égal. Ces variables sont passées à la *tlbimp.exe* et à la *aximp.exe* générées en plus du bloc environnement normal ou en remplacement de manière sélective.|
|`ExecuteAsTool`|Paramètre `Boolean` facultatif.<br /><br /> Si `true` , exécute *tlbimp.exe* et *aximp.exe* à partir de la version cible de .NET Framework appropriée pour générer les assemblys de wrapper nécessaires. Ce paramètre permet le multiciblage.|
|`IncludeVersionInInteropName`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la version de la typelib sera incluse dans le nom du wrapper. Par défaut, il s’agit de `false`.|
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui contient une paire de clés publique/privée.|
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie un élément qui contient une paire de clés publique/privée.|
|`NoClassMembers`|Paramètre `Boolean` facultatif.|
|`ResolvedAssemblyReferences`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les références d’assembly résolues.|
|`ResolvedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers avec leur nom complet sur le disque qui correspondent aux emplacements physiques des bibliothèques de types fournies comme entrée pour cette tâche.|
|`ResolvedModules`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.|
|`SdkToolsPath`|Paramètre <xref:System.String?displayProperty=fullName> facultatif.<br /><br /> Si `ExecuteAsTool` a la valeur `true`, ce paramètre doit être défini sur le chemin des outils du SDK de la version du framework ciblée.|
|`StateFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier cache pour les horodateurs de composant COM. S’il n’est pas présent, chaque exécution régénère tous les wrappers.|
|`TargetFrameworkVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version du framework cible du projet.<br /><br /> Par défaut, il s’agit de `String.Empty`. ce qui signifie qu’il n’existe pas de filtrage pour une référence basée sur le framework cible.|
|`TargetProcessorArchitecture`|Paramètre `String` facultatif.<br /><br /> Spécifie l’architecture de processeur cible préférée. Passé à l’indicateur *tlbimp.exe*/machine après traduction.<br /><br /> La valeur du paramètre doit être un membre de <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|
|`TypeLibFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le chemin du fichier de bibliothèque de types vers les références COM. Les éléments inclus dans ce paramètre peuvent contenir des métadonnées d’élément. Pour plus d’informations, consultez la section [Métadonnées d’élément TypeLibFiles](#typelibfiles-item-metadata) ci-dessous.|
|`TypeLibNames`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les noms de bibliothèques de types à résoudre. Les éléments inclus dans ce paramètre doivent contenir certaines métadonnées d’élément. Pour plus d’informations, consultez la section [Métadonnées d’élément TypeLibNames](#typelibnames-item-metadata) ci-dessous.|
|`WrapperOutputDirectory`|Paramètre `String` facultatif.<br /><br /> Emplacement sur le disque où se trouve l’assembly d’interopérabilité généré. Si ces métadonnées d’élément ne sont pas spécifiée, la tâche utilise le chemin absolu du répertoire où se trouve le fichier projet.|

## <a name="typelibnames-item-metadata"></a>Métadonnées d’élément TypeLibNames

 Le tableau suivant décrit les métadonnées d’élément disponibles pour les éléments passés au paramètre `TypeLibNames`.

|Métadonnées|Description|
|--------------|-----------------|
|`GUID`|Métadonnées d’élément obligatoires.<br /><br /> GUID de la bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche échoue.|
|`VersionMajor`|Métadonnées d’élément obligatoires.<br /><br /> Version principale de la bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche échoue.|
|`VersionMinor`|Métadonnées d’élément obligatoires.<br /><br /> Version secondaire de la bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche échoue.|
|`EmbedInteropTypes`|Métadonnées `Boolean` facultatives.<br /><br />  Si `true`, incorporez les types interop de cette référence directement dans votre assembly au lieu de générer une DLL interop.|
|`LocaleIdentifier`|Métadonnées d’élément facultatives.<br /><br /> Identificateur de paramètres régionaux (LCID) pour la bibliothèque de types. Ceci est spécifié sous la forme d’une valeur sur 32 bits qui identifie la langue préférée par un utilisateur, une région ou une application. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche utilise « 0 » comme identificateur de paramètres régionaux par défaut.|
|`WrapperTool`|Métadonnées d’élément facultatives.<br /><br /> Spécifie l’outil wrapper utilisé pour générer le wrapper d’assembly pour cette bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche utilise « tlbimp » comme outil wrapper par défaut. Les choix disponibles (leur casse n’est pas prise en compte) sont :<br /><br /> -   `Primary` : utilisez cet outil wrapper quand vous voulez utiliser un assembly PIA (Primary Interop Assembly) déjà généré pour le composant COM. Quand vous utilisez cet outil wrapper, ne spécifiez pas un répertoire de sortie du wrapper, car cela provoquerait l’échec de la tâche.<br />-   `TLBImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour le composant COM.<br />-   `AXImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour un contrôle ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Métadonnées d’élément TypeLibFiles

 Le tableau suivant décrit les métadonnées d’élément disponibles pour les éléments passés au paramètre `TypeLibFiles`.

|Métadonnées|Description|
|--------------|-----------------|
|`EmbedInteropTypes`|Paramètre `Boolean` facultatif.<br /><br />  Si `true`, incorporez les types interop de cette référence directement dans votre assembly au lieu de générer une DLL interop.|
|`WrapperTool`|Métadonnées d’élément facultatives.<br /><br /> Spécifie l’outil wrapper utilisé pour générer le wrapper d’assembly pour cette bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche utilise « tlbimp » comme outil wrapper par défaut. Les choix disponibles (leur casse n’est pas prise en compte) sont :<br /><br /> -   `Primary` : utilisez cet outil wrapper quand vous voulez utiliser un assembly PIA (Primary Interop Assembly) déjà généré pour le composant COM. Quand vous utilisez cet outil wrapper, ne spécifiez pas un répertoire de sortie du wrapper, car cela provoquerait l’échec de la tâche.<br />-   `TLBImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour le composant COM.<br />-   `AXImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour un contrôle ActiveX.|

> [!NOTE]
> Plus vous fournissez d’informations pour identifier de façon univoque une bibliothèque de types, plus grande est la possibilité que la tâche aboutisse au fichier correct sur le disque.

## <a name="remarks"></a>Remarques

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base de tâche](../msbuild/task-base-class.md).

La DLL COM n’a pas besoin d’être inscrite sur la machine pour que cette tâche fonctionne.

## <a name="msb4803-error"></a>Erreur MSB4803

Si vous essayez d’exécuter un projet qui utilise la `ResolveCOMReference` tâche à partir des `dotnet` commandes CLI, vous recevez l’erreur :

```output
MSB4803: The task "ResolveComReference" is not supported on the .NET Core version of MSBuild. Please use the .NET Framework version of MSBuild.
```

Cette tâche n’est pas prise en charge sur la version .NET Core de MSBuild, qui est utilisée lorsque vous exécutez la `dotnet build` commande à partir de la ligne de commande. Essayez de générer le projet en appelant [MSBuild.exe](msbuild-command-line-reference.md) à partir de la invite de commandes développeur Visual Studio, car cela utilise la version .NET Framework de MSBuild.

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
