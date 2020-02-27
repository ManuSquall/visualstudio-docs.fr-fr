---
title: WriteAllTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630676"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Écrit les journaux de suivi pour tous les threads et tous les contextes.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Paramètres

[in] `intermediateDirectory`

 Répertoire où stocker le journal de suivi.

[in] `tlogRootName`

 Nom racine du nom du fichier journal.

## <a name="return-value"></a>Valeur retournée

 **HRESULT** avec le bit **SUCCEEDED** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker. h*

## <a name="see-also"></a>Voir aussi

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)