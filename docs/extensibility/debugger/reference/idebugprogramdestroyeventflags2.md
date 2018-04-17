---
title: IDebugProgramDestroyEventFlags2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6b57206159ce00fbb79e9f9af1a6353588df76c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permet à un moteur de débogage substituer le comportement par défaut de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur lorsque vous arrêtez une session de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par les moteurs de débogage. Il est utile pour les hôtes qui peuvent créer et détruire plusieurs programmes pendant la durée de vie d’un processus.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugProgramDestroyEventFlags2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Récupère le programme détruire des indicateurs.|  
  
## <a name="remarks"></a>Notes  
 Le comportement par défaut de le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] est de l’interface utilisateur pour revenir au mode Création après que tous les programmes ont envoyées à un programme détruire l’événement. Cette interface permet à un moteur de débogage modifier ce comportement.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll