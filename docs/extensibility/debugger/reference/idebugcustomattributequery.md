---
title: IDebugCustomAttributeQuery ( france) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 598db5ad711c8b61339e188311c1a437a24d013c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732613"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Représente une requête pour les attributs personnalisés sur une méthode ou un type.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Méthodes
 Cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Récupère un attribut personnalisé donné son nom.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Détermine dans l’attribut personnalisé spécifié est défini.|

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
