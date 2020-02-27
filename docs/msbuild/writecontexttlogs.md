---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf34ff63b00cf523ba9ef704f4417be4d5cdbf77
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630703"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Écrit des fichiers journaux pour le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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

- [WriteAllTLogs](../msbuild/writealltlogs.md)