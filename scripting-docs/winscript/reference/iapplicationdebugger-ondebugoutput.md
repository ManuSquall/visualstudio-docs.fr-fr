---
title: 'IApplicationDebugger :: onDebugOutput | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebugOutput
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebugOutput
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ebbb7fb9f69af2f0977434a29015d79e8cf9178
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577845"
---
# <a name="iapplicationdebuggerondebugoutput"></a>IApplicationDebugger::onDebugOutput
Gère un événement de sortie de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstr`  
 dans Chaîne à afficher dans le débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le débogueur affiche généralement `pstr` dans une fenêtre de sortie.  
  
 Cette méthode est appelée lorsque `IDebugApplication::DebugOutput` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)