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
ms.openlocfilehash: 3acdaabffc35122616cced4113abbc5a43beb9a1
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481973"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash, tâche

Vérifie qu’un fichier correspond au hachage de fichier attendu.

Cette tâche a été ajoutée dans la version 15.8, mais nécessite une [solution de contournement](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pour une utilisation avec les versions de MSBuild antérieures à 16.0.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `VerifyFileHash` .

|Paramètre|Description|
|---------------|-----------------|
|`File`|Paramètre `String` requis.<br /><br />Fichier à hacher et à valider.|
|`Hash`|Paramètre `String` requis.<br /><br />Hachage attendu du fichier.|
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