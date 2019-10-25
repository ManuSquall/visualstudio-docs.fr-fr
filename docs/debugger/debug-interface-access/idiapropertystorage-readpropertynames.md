---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742867"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Récupère les noms de chaîne correspondants pour les identificateurs de propriété donnés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Paramètres
 `cpropid`

dans Nombre d’ID de propriété dans `rgpropid`.

 `rgpropid`

dans Tableau d’ID de propriété pour lequel obtenir les noms (`PROPID` est défini dans WTypes. h en tant que `ULONG`).

 `rglpwstrName`

[in, out] Tableau de noms de propriété pour les ID de propriété spécifiés. Le tableau doit être pré-alloué pour contenir le nombre demandé de noms de propriétés et doit pouvoir contenir au moins `cpropid``BSTR` chaînes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les noms de propriété retournés doivent être libérés (en appelant la fonction `SysFreeString`) lorsqu’ils ne sont plus nécessaires.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)