---
title: IDebugGenericFieldDefinition - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 019633b62d46f6a8ac68e6f5f4abc888e6986ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728197"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Représente la définition d’un champ pour un type générique de code géré.

## <a name="syntax"></a>Syntaxe

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Méthodes
 Cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Construit une instance de terrain compte tenu d’un éventail d’arguments de type.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Récupère les paramètres de type compte tenu du nombre de paramètres.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Récupère le nombre de paramètres de type associés au champ générique.|

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
