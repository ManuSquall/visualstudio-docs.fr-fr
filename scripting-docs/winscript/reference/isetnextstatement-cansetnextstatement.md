---
title: ISetNextStatement::CanSetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb65faaf107c42b44201ea18c1150f8093b1654c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158943"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Cette méthode détermine si le point d’exécution, qui détermine l’instruction suivante de code qui doit être exécuté, peut être défini à l’emplacement spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|L’instruction suivante peut être mis à jour dans le contexte de code spécifié.|  
|`S_FALSE`|L’instruction suivante ne peut pas être mis à jour dans le contexte de code spécifié.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)