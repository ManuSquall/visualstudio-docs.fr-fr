---
title: VerifyFileHash, tâche | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf7738019680085020b9650094931d5860bc29b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618378"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash, tâche

Vérifie qu’un fichier correspond au hachage de fichier attendu.

Cette tâche a été ajoutée dans la version 15.8, mais nécessite une [solution de contournement](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pour une utilisation avec les versions de MSBuild antérieures à 16.0.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `VerifyFileHash` .

|Paramètre|Description|
|---------------|-----------------|
|`File`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br />Fichiers à hacher et à valider.|
|`Hash`|Paramètre `String` requis.<br /><br />Hachage attendu du fichier.|
|`Items`|Paramètre de sortie de <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br />Entrée `Files` avec des métadonnées supplémentaires définies sur le hachage du fichier.|
|`Algorithm`|Paramètre `String` facultatif.<br /><br />Algorithme. Valeurs autorisées : `SHA256`, `SHA384`, `SHA512`. Valeur par défaut = `SHA256`.|
|`HashEncoding`|Paramètre `String` facultatif.<br /><br />Encodage à utiliser pour les hachages générés. La valeur par défaut est `hex`. Valeurs autorisées = `hex`, `base64`.|

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `VerifyFileHash` pour vérifier sa propre somme de contrôle.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)