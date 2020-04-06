---
title: IDebugProperty2::GetExtendedInfo (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721489"
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
[dans] GUID qui détermine le type d’informations étendues à récupérer. Pour plus de détails, consultez la section Notes.

`pExtendedInfo`\
[out] Renvoie `VARIANT` un objet ou un objet (C) qui peut être utilisé pour récupérer les informations de propriété étendues. Par exemple, ce paramètre peut retourner une `IUnknown` interface qui peut être interrogée pour une interface [IDebugDocumentText2.](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Pour plus de détails, consultez la section Notes.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur. Retourne `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` s’il n’y a pas d’informations étendues à récupérer.

## <a name="remarks"></a>Notes
 Cette méthode existe dans le but de récupérer des informations qui ne se prêtent pas à être récupérées en appelant la méthode [GetPropertyInfo.](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

 Les GUID suivants sont généralement reconnus par cette méthode (les valeurs GUID sont spécifiées pour C’puisque le nom n’est disponible dans aucune assemblée). Des GUID supplémentaires peuvent être créés pour une utilisation interne.

|Nom|GUID|Description|
|----------|----------|-----------------|
|guidDocument|3f98de84-fee9-11d0-b47f-00a0244a1dd2|Retourne `IUnknown` une interface sur le document. Typiquement, l’interface [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) peut `IUnknown` être obtenue à partir de cette interface.|
|guidCodeContexte|e2fc65e-56ce-11d1-b528-00aax004a8797|Renvoie `IUnknown` une interface dans le contexte du document. Typiquement, l’interface [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) peut `IUnknown` être obtenue à partir de cette interface.|
|guidCustomViewerSupported|D9c9da31-ffbe-4eeb-9186-23121e3c088c|Renvoie une chaîne contenant le CLSID d’un spectateur personnalisé, généralement implémenté par un évaluateur d’expression.|
|guidExtendedInfoSlot|6df235ad-82c6-4292-9c97-7389770bc42f|Retourne un numéro de 32 bits représentant le numéro de fente souhaité si cette propriété représente une adresse locale de code géré.|
|guidExtendedInfoSignature|b5fb6d46-f805-417f-96a3-8ba737073ffd|Retourne une chaîne contenant la signature de la variable associée à l’objet de propriété.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
