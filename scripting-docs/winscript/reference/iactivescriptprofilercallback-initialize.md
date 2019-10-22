---
title: 'IActiveScriptProfilerCallback :: Initialize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576442"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Appelé pour initialiser l’objet de profileur chaque fois que le profilage est démarré sur un moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwContext`  
 dans Valeur de 4 octets qui est passée à [IActiveScriptProfilerControl :: StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Si la méthode ne peut pas initialiser l’objet de profileur, elle doit retourner un HRESULT d’échec pour notifier le moteur de script. Dans ce cas, le moteur de script doit appeler directement [IActiveScriptProfilerCallback :: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), en passant le HRESULT dans le paramètre, puis libérer l’objet de profileur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)