---
title: WriteContextTLogs | Microsoft Docs
description: En savoir plus sur la syntaxe, les exigences et la valeur de retour pour WriteContextTLogs, qui écrit les fichiers journaux du contexte actuel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b44777f41c4fac3d36cb79222d48a93c5c1cf0b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888002"
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

 **HRESULT** avec le bit **Succeeded** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [WriteAllTLogs](../msbuild/writealltlogs.md)