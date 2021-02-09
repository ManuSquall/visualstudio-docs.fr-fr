---
title: 'IDebugProperty2 :: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bb9fe21b1dc004d5a124a1146e6f7610fbe8699
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916058"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Obtient des informations étendues pour la propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Paramètres
`guidExtendedInfo`\
dans GUID qui détermine le type d’informations étendues à récupérer. Pour plus de détails, consultez la section Notes.

`pExtendedInfo`\
à Retourne un `VARIANT` (C++) ou un objet (C#) qui peut être utilisé pour récupérer les informations sur les propriétés étendues. Par exemple, ce paramètre peut retourner une `IUnknown` interface qui peut être interrogée pour une interface [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) . Pour plus de détails, consultez la section Notes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur. Retourne `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` s’il n’y a pas d’informations étendues à récupérer.

## <a name="remarks"></a>Notes
 Cette méthode existe dans le but de récupérer des informations qui ne se prêtent pas à être récupérées en appelant la méthode [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

 Les GUID suivants sont généralement reconnus par cette méthode (les valeurs GUID sont spécifiées pour C# puisque le nom n’est pas disponible dans un assembly). Des GUID supplémentaires peuvent être créés pour une utilisation interne.

|Nom|GUID|Description|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Retourne une `IUnknown` interface au document. En règle générale, l’interface [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) peut être obtenue à partir de cette `IUnknown` interface.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Retourne une `IUnknown` interface au contexte de document. En règle générale, l’interface [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) peut être obtenue à partir de cette `IUnknown` interface.|
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Retourne une chaîne contenant le CLSID d’une visionneuse personnalisée, généralement implémentée par un évaluateur d’expression.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Retourne un nombre 32 bits représentant le numéro d’emplacement souhaité si cette propriété représente une adresse locale de code managé.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Retourne une chaîne contenant la signature de la variable associée à l’objet de propriété.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
