---
title: 'IDebugProperty :: EnumMembers, | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562425"
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
 dans Spécifie les constantes de `DBGPROP_INFO_FLAGS` qui déterminent les champs dans les structures de propriété de débogage énumérées à remplir.  
  
 `nRadix`  
 dans Base à utiliser pour interpréter toutes les informations numériques.  
  
 `refiid`  
 dans Cet IID est passé pour filtrer l’énumérateur. L’IID est l’une des interfaces `IDebugPropertyEnumType` qui héritent de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 à Retourne l’interface `IEnumDebugPropertyInfo` qui énumère les propriétés de membre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 @No__t_1 de l' [interface IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)  
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)