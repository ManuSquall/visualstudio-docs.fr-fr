---
title: 'IProvideExpressionContexts :: EnumExpressionContexts | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572388"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Retourne un énumérateur de contextes d’expression connus par ce composant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppedec`  
 à Énumérateur de contextes d’expression connus par ce composant.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le gestionnaire de débogage de processus utilise cette méthode pour rechercher tous les contextes d’expression globaux associés à un thread donné.  
  
> [!NOTE]
> Cette méthode est appelée à partir du thread d’intérêt. Il revient à l’implémenteur d’identifier le thread actuel et de retourner un énumérateur approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)