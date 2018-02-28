---
title: IDebugApplication::DebugOutput | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc956c7d2d65d20788a79c9f685e386aba97a80
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Provoque la chaîne donnée à afficher par l’environnement de développement intégré (IDE) de débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstr`  
 [in] Chaîne à afficher dans le débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode permet à un moteur de langage implémenter le support de sortie de débogage spécifiques à une langue. La chaîne est généralement affichée dans la fenêtre de sortie du débogueur.  
  
 Cette méthode provoque `IApplicationDebugger::onDebugOutput` à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)