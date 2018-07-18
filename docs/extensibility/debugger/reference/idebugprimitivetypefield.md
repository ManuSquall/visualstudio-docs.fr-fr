---
title: IDebugPrimitiveTypeField | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98be0b9fd3884db3e42bd1dc33b4f9dbb78d3ee1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114980"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Représente une valeur d’énumération de type primitif d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Récupère le type primitif associé à ce champ.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll