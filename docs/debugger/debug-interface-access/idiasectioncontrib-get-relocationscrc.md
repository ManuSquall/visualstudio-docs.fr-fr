---
title: IDiaSectionContrib::get_relocationsCrc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relocationsCrc method
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8602cfefbd414561ebfbaee979e6af5711b879
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742548"
---
# <a name="idiasectioncontribget_relocationscrc"></a>IDiaSectionContrib::get_relocationsCrc
Récupère la vérification de redondance cyclique (CRC) des informations de réadressage pour la section.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relocationsCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le CRC des informations de réadressage pour la section.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)