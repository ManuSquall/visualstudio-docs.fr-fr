---
title: Méthode IJsDebugProperty::GetPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85dd11fbd5b7f012dc47e170ee785e671d6a7f14
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086708"
---
# <a name="ijsdebugpropertygetpropertyinfo-method"></a>IJsDebugProperty::GetPropertyInfo, méthode
Obtient des informations pour cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nRadix`  
 [in] Base à utiliser.  
  
 `pPropertyInfo`  
 [out] Informations sur l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)