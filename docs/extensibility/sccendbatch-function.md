---
title: SccEndBatch fonction) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700921"
---
# <a name="sccendbatch-function"></a>SccEndBatch fonction)
Cette fonction conclut un lot d’opérations de contrôle de code source. Ces lots ne peuvent pas être imbriqués.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Traitement des opérations réussi.|
|SCC_E_UNKNOWNERROR|Échec non spécifique.|

## <a name="remarks"></a>Notes
 Les lots de contrôle de code source sont utilisés pour exécuter les mêmes opérations de contrôle de code source sur plusieurs projets ou plusieurs contextes. Les lots peuvent être utilisés pour éliminer les boîtes de dialogue redondantes de l’expérience utilisateur pendant une opération par lot. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et la `SccEndBatch` fonction sont utilisés comme une paire pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriqués.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
