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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578650"
---
# <a name="getfilehash-task"></a>GetFileHash, tâche

Calcule les sommes de contrôle du contenu d’un fichier ou d’un ensemble de fichiers.

Cette tâche a été ajoutée dans la version 15.8, mais nécessite une [solution de contournement](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pour une utilisation avec les versions de MSBuild antérieures à 16.0.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `GetFileHash`.

|Paramètre|Description|
|---------------|-----------------|
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br />Fichiers à hacher.|
|`Items`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Entrée `Files` avec des métadonnées supplémentaires définies sur le hachage du fichier.|
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

- [Tâches :](../msbuild/msbuild-tasks.md)

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)