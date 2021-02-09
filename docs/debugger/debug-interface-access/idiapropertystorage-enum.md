---
title: IDiaPropertyStorage::Enum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8972fa93ebae30fc64839324106d068e27577434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864648"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Obtient un énumérateur pour les propriétés dans cet ensemble.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 `ppenum`

à Retourne un `IEnumSTATPROPSTG` objet (dans l’espace de noms Microsoft. VisualStudio. OLE. Interop) représentant une énumération de propriétés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)