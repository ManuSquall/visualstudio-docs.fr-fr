---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572580"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Utilisé pour spécifier `DebugPropertyInfo` champs  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Membres  
 DBGPROP_INFO_NAME  
 Initialise le champ `bstrName`.  
  
 DBGPROP_INFO_TYPE  
 Initialise le champ `bstrType`.  
  
 DBGPROP_INFO_VALUE  
 Initialise le champ `bstrValue`.  
  
 DBGPROP_INFO_FULLNAME  
 Initialise le champ `bstrFullName`.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Initialise le champ `dwAttrib`.  
  
 DBGPROP_INFO_DEBUGPROP  
 Initialise le champ `pDebugProp` qui contient une interface `IDebugProperty`.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Spécifie que le champ de valeur doit contenir la valeur développée automatiquement, si elle est disponible, pour ce type d’objet.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de la [structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)