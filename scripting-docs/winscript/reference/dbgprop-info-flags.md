---
title: DBGPROP_INFO_FLAGS | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
f1_keywords: DBGPROP_INFO_FLAGS
helpviewer_keywords: DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9821cde6c159712ff44438b74eea0f8e01247155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Permet de spécifier `DebugPropertyInfo` champs  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Initialise le `pDebugProp` champ contenant une `IDebugProperty` interface.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Spécifie que le champ de valeur doit contenir la valeur auto-développé, s’il est disponible pour ce type d’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [DebugPropertyInfo (Structure)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)