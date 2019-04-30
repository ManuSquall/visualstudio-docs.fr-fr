---
title: IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87913f15f8799be0ad3f6616eeea53a8a627e3d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963453"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Ignore un nombre spécifié de `ExtendedDebugPropertyInfo` structures dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de `ExtendedDebugPropertyInfo` structures dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`. Retourne `S_FALSE` et définit le pointeur d’élément actuel à la fin de l’énumération si `celt` est supérieur au nombre d’éléments à gauche dans l’énumérateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugExtendedPropertyInfo Interface](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)