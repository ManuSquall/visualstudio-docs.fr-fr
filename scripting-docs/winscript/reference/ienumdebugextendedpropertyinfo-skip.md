---
title: 'IEnumDebugExtendedPropertyInfo :: Skip | Microsoft Docs'
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
ms.openlocfilehash: 8e5c187f3484154a2758b67300c98d4cb9fc9023
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574241"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Ignore un nombre spécifié de structures de `ExtendedDebugPropertyInfo` dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 dans Nombre de structures de `ExtendedDebugPropertyInfo` dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`. Retourne `S_FALSE` et définit le pointeur d’élément actuel à la fin de l’énumération si `celt` est supérieur au nombre d’éléments restants dans l’énumérateur.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)  
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)