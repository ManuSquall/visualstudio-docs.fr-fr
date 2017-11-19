---
title: EX_DBGPROP_INFO_FLAGS | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EX_DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
helpviewer_keywords: EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0af0de81c0253b72fe432cb3cefe11c362bc2ec4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
Permet de spécifier `ExtendedDebugPropertyInfo` champs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>Membres  
 EX_DBGPROP_INFO_ID  
 Initialise l’identificateur de la propriété.  
  
 EX_DBGPROP_INFO_NTYPE  
 Initialise le type de la propriété.  
  
 EX_DBGPROP_INFO_NVALUE  
 Initialise la valeur de la propriété.  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 Initialise le `plb` champ.  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 Initialise le `pDebugExtProp` champ contenant une `IDebugExtendedProperty` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [ExtendedDebugPropertyInfo (Structure)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [Interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)