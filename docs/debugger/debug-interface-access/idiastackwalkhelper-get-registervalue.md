---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275941aaf3a1eb2cab6554b18c6d9aa66605121a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831830"
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
Récupère la valeur d’un Registre.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `index`

[in] Une valeur comprise entre le [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md) énumération spécifiant permettant d’obtenir la valeur de Registre.

 `pRetVal`

[out] Retourne la valeur actuelle du Registre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 En dépit de la taille de la `pRetVal` paramètre, une implémentation doit stocker uniquement ce que le Registre normalement conserve. Par exemple, un Registre de 8 bits conserve uniquement les 8-bits les plus bas de la valeur donnée. Cette valeur de 8 bits est développée à 64 bits lorsque retourné par cette méthode.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)