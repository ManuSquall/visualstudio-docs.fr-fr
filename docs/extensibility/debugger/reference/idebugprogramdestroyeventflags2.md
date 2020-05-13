---
title: IDebugProgramDestroyEventFlags2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722507"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permet à un moteur débogé de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] remplacer le comportement par défaut de l’interface utilisateur lorsque vous terminez une session de débogé.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par les moteurs de débogé. Il est utile pour les hôtes qui pourraient créer et détruire plusieurs programmes au cours de la durée de vie d’un processus.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugProgramDestroyEventFlags2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Récupère le programme détruire les drapeaux.|

## <a name="remarks"></a>Notes
 Le comportement par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] défaut de l’interface utilisateur est de revenir en mode de conception après que tous les programmes ont envoyé un événement de destruction de programme. Cette interface permet à un moteur de débogé de changer ce comportement.

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
