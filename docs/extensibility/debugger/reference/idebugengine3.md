---
title: IDebugEngine3 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 291f5ca6f945abe9e0322839eb80c38b60674ce4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114415"
---
# <a name="idebugengine3"></a>IDebugEngine3
Représente un moteur de débogage (DE) qui contrôle le débogage d’un ou plusieurs modules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par un DE personnalisés (si elle prend en charge les symboles) pour activer l’état JustMyCode. Cette interface doit être implémentée par le DE si elle prend en charge les symboles et JustMyCode.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est appelée par le Gestionnaire de session de débogage (SDM) pour passer des options utilisateur pour les emplacements à partir desquels charger les symboles. Il est également appelé pour définir le GUID du moteur de lorsqu’il est instancié (ce GUID est basé sur les mesures à partir du moment de l’enregistrement du moteur). Le SDM appelle également cette interface pour définir l’état JustMyCode et définir toutes les exceptions connues par le débogueur à un état spécifique.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), le `IDebugEngine3` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Définit le chemin d’accès ou les chemins d’accès que le DE permet de rechercher les symboles de débogage.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Charge les symboles pour tous les modules qui n’ont pas encore été chargé des symboles.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indique le DE sur les informations JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Définit le GUID D’à partir de la métrique.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Définissez toutes les exceptions actuellement en attente à un état spécifique.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)