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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 722d8c42786a7aaa2daae293b96f7926abcc90ca
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719832"
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

## <a name="return-value"></a>Valeur de retour
 **HRESULT** avec le bit **SUCCEEDED** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Spécifications
 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi
- [WriteAllTLogs](../msbuild/writealltlogs.md)