---
title: 'IEnumDebugExpressionContexts :: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Clone
ms.assetid: c8070ae1-120c-4b5d-bd3d-ae8fca6f9277
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70e11ec9af8859b0e1d4ecd10bd52c8c573de930
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577155"
---
# <a name="ienumdebugexpressioncontextsclone"></a>IEnumDebugExpressionContexts::Clone
Crée un énumérateur qui contient le même État que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppedec`  
 à Retourne l’interface `IEnumDebugExpressionContexts` du clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un énumérateur qui contient le même État que l’énumérateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)