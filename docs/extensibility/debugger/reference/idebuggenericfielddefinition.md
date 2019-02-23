---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea197cf5b6207117007c5d6d95b742e3a892223b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683335"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Représente la définition d’un champ pour un type générique du code managé.

## <a name="syntax"></a>Syntaxe

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Méthodes
 Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Construit une instance du champ étant donnée un tableau d’arguments de type.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Récupère les paramètres de type étant données le nombre de paramètres.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Récupère le nombre de paramètres de type associé au champ générique.|

## <a name="requirements"></a>Spécifications
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll