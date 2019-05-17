---
title: IRemoteDebugApplicationEx:RevokeBreak | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:RevokeBreak
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:RevokeBreak
ms.assetid: 1f077860-0a39-4ec9-b676-ae0712819c7b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0992eb5637434ccdf0dbf4fa6e436c87ae3fdd6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788402"
---
# <a name="iremotedebugapplicationexrevokebreak"></a>IRemoteDebugApplicationEx:RevokeBreak

Révoque une commande break.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RevokeBreak( );
```

### <a name="parameters"></a>Paramètres

Aucun.

## <a name="return-value"></a>Valeur de retour

La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.

|Value|Description|
|-----------|-----------------|
|`S_OK`|La méthode a réussi.|

## <a name="see-also"></a>Voir aussi

- [Interface IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)