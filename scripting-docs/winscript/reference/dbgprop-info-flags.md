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
ms.openlocfilehash: c63cf941bca1965fc4a2e3997f0c0b50ebc44035
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147590"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Permet de spécifier `DebugPropertyInfo` champs  
  
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
 Initialise le `bstrName` champ.  
  
 DBGPROP_INFO_TYPE  
 Initialise le `bstrType` champ.  
  
 DBGPROP_INFO_VALUE  
 Initialise le `bstrValue` champ.  
  
 DBGPROP_INFO_FULLNAME  
 Initialise le `bstrFullName` champ.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Initialise le `dwAttrib` champ.  
  
 DBGPROP_INFO_DEBUGPROP  
 Initialise le `pDebugProp` champ qui contient un `IDebugProperty` interface.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Spécifie que le champ de valeur doit contenir la valeur auto-développé, s’il est disponible pour ce type d’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [DebugPropertyInfo (Structure)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)