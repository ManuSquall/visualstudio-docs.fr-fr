---
title: 'IDebugProperty :: GetPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562325"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Obtient la valeur d’un `IDebugProperty` qui décrit une méthode ou une propriété indexée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFields`  
 dans Spécifie les constantes de `DBGPROP_INFO_FLAGS` qui déterminent les champs à remplir dans la structure `DebugPropertyInfo`.  
  
 `nRadix`  
 dans Base à utiliser pour mettre en forme les informations numériques.  
  
 `pPropertyInfo`  
 à Retourne la structure `DebugPropertyInfo` qui décrit la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)