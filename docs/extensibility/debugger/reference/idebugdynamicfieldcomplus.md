---
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de22b84bc410b351307c81e5b083e21f5c35704e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986096"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Représente un champ dynamique pour un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Récupère un type en fonction de son type primitif.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Récupère un type en fonction de son jeton.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : SH.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll