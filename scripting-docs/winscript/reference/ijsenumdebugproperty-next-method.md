---
title: Méthode IJsEnumDebugProperty::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ec6a1dded8c24de06a5746261a19b6609a97ada
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977537"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next, méthode
Lit les propriétés de cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `count`  
 [in] Le nombre de propriétés à lire.  
  
 `ppDebugProperty`  
 [out] Objet représentant l’Explorateur de propriétés.  
  
 `pActualCount`  
 [out] Le nombre réel de propriétés de l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)