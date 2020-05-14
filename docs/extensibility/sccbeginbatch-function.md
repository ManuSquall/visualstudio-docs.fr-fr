---
title: Fonction SccBeginBatch (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701201"
---
# <a name="sccbeginbatch-function"></a>Fonction SccBeginBatch
Cette fonction démarre une séquence de lots d’opérations de contrôle des sources. Le [SccEndBatch](../extensibility/sccendbatch-function.md) sera appelé à mettre fin au lot. Ces lots ne peuvent pas être imbriqués.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le lot d’opérations a commencé avec succès.|
|SCC_E_UNKNOWNERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Les lots de contrôle de source sont utilisés pour exécuter les mêmes opérations sur plusieurs projets ou contextes multiples. Les lots peuvent être utilisés pour éliminer les boîtes de dialogue redondantes par projet de l’expérience utilisateur au cours d’une opération en lots. La `SccBeginBatch` fonction et le [SccEndBatch](../extensibility/sccendbatch-function.md) sont utilisés comme une paire de fonctions pour indiquer le début et la fin d’une opération. Ils ne peuvent pas être imbriqués. `SccBeginBatch`définit un drapeau indiquant qu’une opération par lots est en cours.

 Bien qu’une opération par lots soit en vigueur, le plug-in de contrôle source devrait présenter au plus une boîte de dialogue pour toute question à l’utilisateur et appliquer la réponse de cette boîte de dialogue sur toutes les opérations ultérieures.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
