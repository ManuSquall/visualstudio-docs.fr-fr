---
title: IDiaEnumFrameData::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc6e5d42d2a9f360b3899b2922bda879d4293d4d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601601"
---
# <a name="idiaenumframedatagetnewenum"></a>IDiaEnumFrameData::get__NewEnum
Récupère le <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> version de cet énumérateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

[out] Retourne le `IUnknown` interface qui représente le <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> version de cet énumérateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)