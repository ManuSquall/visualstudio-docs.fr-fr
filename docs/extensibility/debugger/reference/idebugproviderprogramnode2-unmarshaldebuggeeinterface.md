---
description: Obtient une interface spécifiée à travers les limites du processus.
title: 'IDebugProviderProgramNode2 :: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f51484ae1e9acbb9b94fe546f8157145673e22f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167865"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtient une interface spécifiée à travers les limites du processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Paramètres
`riid`\
dans GUID de l’interface à obtenir.

`ppvObject`\
à Retourne l’objet implémentant l’interface souhaitée. [C++] cela peut être converti directement en type d’interface souhaité. [C#] Utilisez la <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> méthode pour récupérer l’interface souhaitée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée lorsque le moteur de débogage s’exécute dans l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espace de processus et que le programme en cours de débogage s’exécute dans son propre espace de processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
