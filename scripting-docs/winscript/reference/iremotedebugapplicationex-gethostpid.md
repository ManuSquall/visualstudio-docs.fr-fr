---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 62033169e10585015b5f1439067aa0cbc42447a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754638"
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