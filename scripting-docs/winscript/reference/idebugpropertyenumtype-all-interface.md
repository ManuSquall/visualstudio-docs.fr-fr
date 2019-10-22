---
title: Interface IDebugPropertyEnumType_All | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574319"
---
# <a name="idebugpropertyenumtype_all-interface"></a>IDebugPropertyEnumType_All, interface
Les interfaces `IDebugPropertyEnumType` sont définies de sorte que chacun de leurs IID puisse être passé comme filtre à `IDebugProperty::EnumMembers` lors de la demande de l’énumérateur approprié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Retourne une chaîne de texte décrivant le nom|  
  
 Les interfaces suivantes héritent de `IDebugPropertyEnumType_All` et n’ont aucune méthode supplémentaire.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)