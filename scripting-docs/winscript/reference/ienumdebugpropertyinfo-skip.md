---
title: 'IEnumDebugPropertyInfo :: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574156"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Ignore un nombre spécifié de structures de `DebugPropertyInfo` dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 dans Nombre de structures de `DebugPropertyInfo` dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`. Retourne `S_FALSE` et définit le pointeur d’élément actuel à la fin de l’énumération si `celt` est supérieur au nombre d’éléments restants dans l’énumérateur.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)