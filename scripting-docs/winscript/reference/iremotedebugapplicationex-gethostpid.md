---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d660cce006e7f84f1b1c01f1ec0a406b5c4b9df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934584"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Retourne l’ID de processus pour l’application hôte.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Paramètres

`dwHostPid`

[out] L’identificateur de processus hôte.

## <a name="return-value"></a>Valeur de retour

La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.

|Value|Description|
|-----------|-----------------|
|`S_OK`|La méthode a réussi.|

## <a name="remarks"></a>Notes

Utilisé par l’IDE.

## <a name="see-also"></a>Voir aussi

- [Interface IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)