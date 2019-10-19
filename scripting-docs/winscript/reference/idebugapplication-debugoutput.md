---
title: IDebugApplication ::D ebugOutput | Microsoft Docs
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
ms.openlocfilehash: 7d52acf0e4b32f0ced63b53a6b37ffe62f1d948e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575015"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Provoque l’affichage de la chaîne donnée par l’environnement de développement intégré (IDE) du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DebugOutput(  
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
 Cette méthode permet à un moteur de langage d’implémenter la prise en charge de la sortie de débogage spécifique au langage. La chaîne est généralement affichée dans la fenêtre sortie du débogueur.  
  
 Cette méthode provoque l’appel de `IApplicationDebugger::onDebugOutput`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)