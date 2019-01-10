---
title: Méthode IJsEnumDebugProperty::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9e6b0e3499f9420d42660880f616d2d0873d7a0f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086773"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)