---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad6e7d10b2a6a83aa11a0296f4804704cd12c9d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952448"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface est implémentée par une interface d’extension [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) les implémenteurs. Il permet à l’implémenteur obtenir des informations sur l’environnement de processus de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Implémentez cette interface pour obtenir des informations sur l’environnement d’exécution d’un processus de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProcessQueryProperties`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Requêtes pour une valeur de propriété.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Requêtes pour les valeurs de propriété.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée rarement.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Portpriv.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
