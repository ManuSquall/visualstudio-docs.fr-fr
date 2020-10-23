---
title: DownloadFile, tâche | Microsoft Docs
description: En savoir plus sur les paramètres de la tâche MSBuild DownloadFile, qui télécharge les fichiers spécifiés à l’aide du protocole HTTP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda3edcd1c8bf173e1b70d8bf2d76d58f6e10d8d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436656"
---
# <a name="downloadfile-task"></a>DownloadFile, tâche

Télécharge les fichiers spécifiés à l’aide du protocole HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>La tâche DownloadFile est disponible dans MSBuild 15.8 et versions ultérieures uniquement.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `DownloadFile` .

|Paramètre|Description|
|---------------|-----------------|
|`DestinationFileName`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Nom à utiliser pour le fichier téléchargé.  Par défaut, le nom de fichier est dérivé de `SourceUrl` ou du serveur distant.|
|`DestinationFolder`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le dossier de destination dans lequel télécharger le fichier.  Le dossier est créé s’il n’existe pas.|
|`DownloadedFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le fichier qui a été téléchargé.|
|`Retries`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le nombre de tentatives de téléchargement, si toutes les tentatives précédentes ont échoué. La valeur par défaut est zéro.|
|`RetryDelayMilliseconds`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai en millisecondes entre les tentatives nécessaires. La valeur par défaut est 5 000.|
|`SkipUnchangedFiles`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, ignore le téléchargement des fichiers qui sont inchangés. La valeur par défaut est `true`. La tâche `DownloadFile` considère que les fichiers sont inchangés s’ils ont la même taille et la même heure de dernière modification selon le serveur distant. <br /><br />**Remarque :** Les serveurs HTTP n’indiquent pas tous la date de dernière modification des fichiers, ce qui entraîne un nouveau téléchargement du fichier.|
|`SourceUrl`|Paramètre `String` requis.<br /><br /> Spécifie l’URL à télécharger.|

## <a name="remarks"></a>Remarques

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

L’exemple suivant télécharge un fichier et l’inclut dans les éléments `Content` avant de générer le projet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
