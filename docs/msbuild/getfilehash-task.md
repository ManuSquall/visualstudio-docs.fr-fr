---
title: GetFileHash, tâche | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71ebd50b42408dc7bd2642c257dece686245870f
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55485034"
---
# <a name="getfilehash-task"></a>GetFileHash, tâche

Calcule les sommes de contrôle du contenu d’un fichier ou d’un ensemble de fichiers.

Cette tâche a été ajoutée dans la version 15.8, mais nécessite une [solution de contournement](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pour une utilisation avec les versions de MSBuild antérieures à 16.0.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `GetFileHash` .

|Paramètre|Description|
|---------------|-----------------|
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br />Fichiers à hacher.|
|`Items`|Paramètre de sortie de <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br />Entrée `Files` avec des métadonnées supplémentaires définies sur le hachage du fichier.|
|`Hash`|Paramètre de sortie `String`.<br /><br />Hachage du fichier. Cette sortie est définie seulement si un seul élément a été passé en entrée.|
|`Algorithm`|Paramètre `String` facultatif.<br /><br />Algorithme. Valeurs autorisées : `SHA256`, `SHA384`, `SHA512`. Valeur par défaut = `SHA256`.|
|`MetadataName`|Paramètre `String` facultatif.<br /><br />Nom des métadonnées où le hachage est stocké dans chaque élément. La valeur par défaut est `FileHash`.|
|`HashEncoding`|Paramètre `String` facultatif.<br /><br />Encodage à utiliser pour les hachages générés. La valeur par défaut est `hex`. Valeurs autorisées = `hex`, `base64`.|

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `GetFileHash` pour déterminer et afficher la somme de contrôle des éléments `FilesToHash`.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

[Tâches](../msbuild/msbuild-tasks.md)

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)