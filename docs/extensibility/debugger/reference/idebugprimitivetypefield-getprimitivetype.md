---
title: IDebugPrimitiveTypeField::GetPrimitiveType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a100b02d8a12c70a5fde1a3823035e0f3202586
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932207"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Récupère le type primitif qui est associé à ce champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```csharp  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwType`  
 [out] Valeur à partir de la [CorElementType, énumération](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) qui représente le type primitif.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)