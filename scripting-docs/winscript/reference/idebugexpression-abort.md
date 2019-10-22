---
title: 'IDebugExpression :: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Abort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Abort
ms.assetid: dbdb63c1-6c4a-4cef-bb40-1843495ae167
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 508939b23be53acbff269744ae4035853f977ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575933"
---
# <a name="idebugexpressionabort"></a>IDebugExpression::Abort
Arrête l’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode arrête une évaluation d’expression au plus tôt.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)