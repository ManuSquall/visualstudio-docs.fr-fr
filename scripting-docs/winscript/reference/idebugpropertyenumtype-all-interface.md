---
title: Interface IDebugPropertyEnumType_All | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2dc5bb84125ca0bf3b25f8f9b8cfe1dad6aeb6d9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097004"
---
# <a name="idebugpropertyenumtypeall-interface"></a>IDebugPropertyEnumType_All, interface
Le `IDebugPropertyEnumType` les interfaces sont définies afin que chacun de leurs IID peut être passé en tant que filtre pour `IDebugProperty::EnumMembers` lors de la demande de l’énumérateur approprié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Retourne une chaîne de texte décrivant le nom|  
  
 Les interfaces suivantes héritent `IDebugPropertyEnumType_All`, et n’avoir aucune des méthodes supplémentaires.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)