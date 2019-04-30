---
title: Fonction SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0662e4c4d1d71e2c9ae0e8f40ff21868d6b9a5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433264"
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