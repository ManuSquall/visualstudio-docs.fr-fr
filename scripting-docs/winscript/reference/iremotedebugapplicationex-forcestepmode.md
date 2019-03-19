---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04a2c700d2cac4bcdc845ebf442de29863e87deb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159489"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

Force le débogueur en mode de pas à pas.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>Paramètres

`pStepThread`

[in] Thread pour le moniteur de débogage de processus à l’étape. Si null, PDM efface son thread d’exécution pas à pas.

## <a name="return-value"></a>Valeur de retour

La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.

|Value|Description|
|-----------|-----------------|
|`S_OK`|La méthode a réussi.|

## <a name="see-also"></a>Voir aussi

- [Interface IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)