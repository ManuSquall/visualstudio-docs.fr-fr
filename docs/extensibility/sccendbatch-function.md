---
title: Fonction SccEndBatch (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700921"
---
# <a name="sccendbatch-function"></a>Fonction SccEndBatch
Cette fonction conclut un lot d’opérations de contrôle des sources. Ces lots ne peuvent pas être imbriqués.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Lot d’opérations conclue avec succès.|
|SCC_E_UNKNOWNERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Les lots de contrôle de source sont utilisés pour exécuter les mêmes opérations de contrôle source dans plusieurs projets ou contextes multiples. Les lots peuvent être utilisés pour éliminer les boîtes de dialogue redondantes de l’expérience utilisateur au cours d’une opération en lots. Le [SccBeginBatch](../extensibility/sccbeginbatch-function.md) `SccEndBatch` et la fonction sont utilisés comme une paire pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriqués.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
