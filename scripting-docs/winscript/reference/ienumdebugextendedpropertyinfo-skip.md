---
title: IEnumDebugExtendedPropertyInfo::Skip | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7f686ccaa5a3195b82458cf3ee11f02be104f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Ignore un nombre spécifié de `ExtendedDebugPropertyInfo` structures dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de `ExtendedDebugPropertyInfo` structures dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`. Retourne `S_FALSE` et définit le pointeur d’élément actuel à la fin de l’énumération si `celt` est supérieur au nombre d’éléments à gauche dans l’énumérateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugExtendedPropertyInfo (Interface)](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)