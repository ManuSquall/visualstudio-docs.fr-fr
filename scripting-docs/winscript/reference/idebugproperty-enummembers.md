---
title: IDebugProperty::EnumMembers | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7edf2d2f94519146a81cf94b3bf30946af59bbe9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097030"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Énumère les membres d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFieldSpec`  
 [in] Spécifie le `DBGPROP_INFO_FLAGS` constantes qui déterminent quels champs dans les structures de propriété énumérée de débogage sont doit être renseigné.  
  
 `nRadix`  
 [in] Base pour être utilisées pour interpréter toutes les informations numériques.  
  
 `refiid`  
 [in] Cet IID est passé pour le filtrage de l’énumérateur. IID fait partie de la `IDebugPropertyEnumType` interfaces qui héritent de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Retourne le `IEnumDebugPropertyInfo` interface qui énumère les propriétés de membre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty (Interface)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All (Interface)](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)