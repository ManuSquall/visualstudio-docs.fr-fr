---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86c20e7c6828cfbf3ec31ba5dcbec9c7ee8478df
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706221"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtient une interface spécifiée au-delà des limites de processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

#### <a name="parameters"></a>Paramètres
 `riid`

 [in] GUID de l’interface à obtenir.

 `ppvObject`

 [out] Retourne l’objet qui implémente l’interface souhaitée. [C++] Cela peut être casté directement au type d’interface souhaitée. [C#] utiliser le <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> méthode pour obtenir l’interface souhaitée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée lorsque le moteur de débogage est en cours d’exécution le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espace de processus et le programme en cours de débogage s’exécute dans son propre espace de processus.

## <a name="see-also"></a>Voir aussi
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)