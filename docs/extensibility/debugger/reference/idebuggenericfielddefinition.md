---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ff7c28a30ccab43629636f7dcd9391a669a376ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884791"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Représente la définition d’un champ pour un type générique de code managé.

## <a name="syntax"></a>Syntaxe

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Méthodes
 Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Construit une instance de champ en fonction d’un tableau d’arguments de type.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Récupère les paramètres de type en fonction du nombre de paramètres.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Récupère le nombre de paramètres de type associés au champ générique.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
