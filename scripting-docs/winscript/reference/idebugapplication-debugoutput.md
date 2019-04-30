---
title: IDebugApplication::DebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a67a16e3fd4868726087df6f2596571d14630f80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990968"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Provoque la chaîne donnée à afficher par l’environnement de développement intégré (IDE) de débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstr`  
 [in] Chaîne à afficher dans le débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet un moteur de langage implémenter la prise en charge de sortie débogage spécifiques au langage. La chaîne est généralement affichée dans la fenêtre de sortie du débogueur.  
  
 Cette méthode provoque `IApplicationDebugger::onDebugOutput` à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)