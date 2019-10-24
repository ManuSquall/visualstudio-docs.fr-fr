---
title: IDiaSectionContrib::get_dataCrc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_dataCrc method
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8287202efaf1f60743969007b432829940441a22
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742691"
---
# <a name="idiasectioncontribget_datacrc"></a>IDiaSectionContrib::get_dataCrc
Récupère le contrôle de redondance cyclique (CRC) des données dans la section.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_dataCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le CRC des données dans la section.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)