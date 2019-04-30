---
title: EX_DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 086a2b7544a95a302219ddc62c15c5b31dd1d9b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955229"
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
Permet de spécifier `ExtendedDebugPropertyInfo` champs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 Initialise l’identificateur de propriété.  
  
 EX_DBGPROP_INFO_NTYPE  
 Initialise le type de la propriété.  
  
 EX_DBGPROP_INFO_NVALUE  
 Initialise la valeur de la propriété.  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 Initialise le `plb` champ.  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 Initialise le `pDebugExtProp` champ qui contient un `IDebugExtendedProperty` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [ExtendedDebugPropertyInfo (Structure)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [Interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)