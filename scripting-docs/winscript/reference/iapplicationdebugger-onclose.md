---
title: 'IApplicationDebugger :: onClose | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577871"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
Gère un événement de fermeture d’application de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque `IDebugApplication::Close` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)