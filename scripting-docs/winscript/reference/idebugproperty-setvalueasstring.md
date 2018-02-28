---
title: IDebugProperty::SetValueAsString | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.SetValueAsString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88a7cba4ec83c5428dd4da4a23ce554702177e76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
Définit la valeur d’une propriété à partir d’une chaîne donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszValue`  
 [in] La valeur à définir.  
  
 `nRadix`  
 [in] Base à utiliser pour l’interprétation des informations numériques.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)