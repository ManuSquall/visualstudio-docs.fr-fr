---
title: Fonction SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e915a2e0c508e62a8d34d8d8a5b4fdcd734bbf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353691"
---
# <a name="sccendbatch-function"></a>Fonction SccEndBatch
Cette fonction termine un lot d’opérations de contrôle de code source. Ces lots ne peuvent pas être imbriqués.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Lot d’opérations conclu avec succès.|
|SCC_E_UNKNOWNERROR|Erreur non spécifique.|

## <a name="remarks"></a>Notes
 Lots de contrôle source sont utilisés pour exécuter les mêmes opérations de contrôle de source entre plusieurs projets ou de plusieurs contextes. Lots peuvent être utilisés pour éliminer les boîtes de dialogue redondante à partir de l’expérience utilisateur lors d’une opération par lot. Le [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et `SccEndBatch` (fonction) sont utilisés en tant que paire pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriquées.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)