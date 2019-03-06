---
title: IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97ca8b06a480d2fddb2002a0b9a19f878caa58f5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610721"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
Appelé lorsqu’un fichier .dbg de candidat a été ouvert.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT NotifyOpenDBG ( 
   LPCOLESTR dbgPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Paramètres
 `dbgPath`

[in] Le chemin d’accès complet du fichier .dbg.

 `resultCode`

[in] Code qui indique la réussite (`S_OK`) ou l’échec de la charge appliquée à ce fichier.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le code de retour est généralement ignoré.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)