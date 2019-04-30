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
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537353"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Récupère correspondant de noms de chaîne pour donné des identificateurs de propriété.

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

[in] Nombre d’ID de propriété dans `rgpropid`.

 `rgpropid`

[in] Tableau d’ID de propriété pour laquelle obtenir les noms (`PROPID` est défini dans WTypes.h comme un `ULONG`).

 `rglpwstrName`

[in, out] Tableau des noms de propriété pour les ID de propriété spécifiée. Le tableau doit être alloué pour contenir le nombre demandé de noms de propriétés au préalable et doit être en mesure de contenir au moins `cpropid``BSTR` chaînes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les noms de propriété retournée doivent être libérées (en appelant le `SysFreeString` (fonction)) lorsqu’ils ne sont plus nécessaires.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)