---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 7110a69c84a131a600c903ac73fbb6acdde7cd64
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913434"
---
# <a name="idebugengine3"></a>IDebugEngine3
Représente un moteur de débogage unique (dé) qui contrôle le débogage d’un ou plusieurs modules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par un DE personnalisé (si elle prend en charge les symboles) pour activer l’état JustMyCode. Cette interface doit être implémentée par le DE si elle prend en charge les symboles et JustMyCode.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est appelée par le Gestionnaire de session de débogage (SDM) pour passer des options utilisateur pour les emplacements à partir desquels charger des symboles. Il est également appelée pour définir le GUID du moteur de lorsqu’il est instancié (ce GUID est basé sur les mesures à partir du moment de l’inscription du moteur). Le SDM appelle également cette interface pour définir l’état JustMyCode et pour définir toutes les exceptions connues par le débogueur à un état spécifique.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), le `IDebugEngine3` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Définit le chemin d’accès ou les chemins d’accès qui le DE permet de rechercher de symboles de débogage.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Charge les symboles pour tous les modules qui n’ont pas encore été chargé des symboles.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indique le DE sur les informations JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Définit le GUID D’à partir des métriques.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Définir toutes les exceptions actuellement en attente sur un état spécifié.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)