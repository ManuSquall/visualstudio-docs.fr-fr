---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2dd18408235a5621354531a2fd228ff44a19d6a1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088710"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Retourne un énumérateur des contextes d’expression connus par ce composant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppedec`  
 [out] Énumérateur des contextes d’expression connus par ce composant.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire de débogage de processus utilise cette méthode pour rechercher tous les contextes d’expression globale associées à un thread donné.  
  
> [!NOTE]
>  Cette méthode est appelée à partir du thread d’intérêt. Il est à l’implémenteur pour identifier le thread actuel et retourne un énumérateur approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)