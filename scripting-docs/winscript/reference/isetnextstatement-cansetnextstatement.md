---
title: ISetNextStatement::CanSetNextStatement | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd32ddf73076f9e29ca3377186ff64be256b8fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Cette méthode détermine si le point d’exécution, qui détermine l’instruction suivante de code à exécuter, peut être défini à l’emplacement spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStackFrame`  
 [in] Pointeur vers un objet de frame de pile.  
  
 `pCodeContext`  
 [in] Pointeur vers un objet de contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’instruction suivante peut être mis à jour dans le contexte de code spécifié.|  
|`S_FALSE`|L’instruction next ne peut pas être mis à jour dans le contexte de code spécifié.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)