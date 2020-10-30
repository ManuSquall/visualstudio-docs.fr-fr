---
title: WriteAllTLogs | Microsoft Docs
description: En savoir plus sur la syntaxe, les exigences et la valeur de retour pour WriteAllTLogs, qui écrit les journaux de suivi pour tous les threads et les contextes.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 754b34b872ba0f0f677a194194b2ff893e7107e1
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047477"
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

 **HRESULT** avec le bit **Succeeded** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)