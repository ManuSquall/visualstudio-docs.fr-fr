---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3cb5c94c55709f5ecdbd6bae63ee3366f3dfeb2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790852"
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