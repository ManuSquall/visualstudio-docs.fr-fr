---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74810aab2f47a36c716891fd45b7424eb737b142
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948944"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient les informations étendues pour la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Paramètres  
 `guidExtendedInfo`  
 [in] GUID qui détermine le type d’informations étendues à récupérer. Pour plus d’informations, consultez la section Notes.  
  
 `pExtendedInfo`  
 [out] Retourne un `VARIANT` (C++) ou un objet (C#) qui peut être utilisé pour récupérer les informations de propriété étendue. Par exemple, ce paramètre peut retourner un `IUnknown` interface qui peut être interrogé pour une [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface. Pour plus d’informations, consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Retourne `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` s’il n’existe aucune informations étendues à récupérer.  
  
## <a name="remarks"></a>Notes  
 Cette méthode existe à des fins de récupération des informations qui ne se prêtent pas à être récupéré en appelant le [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode).  
  
 Les GUID suivantes sont généralement reconnus par cette méthode (les valeurs GUID sont spécifiés pour c#, car le nom n’est pas disponible dans n’importe quel assembly). GUID supplémentaires peut être créés pour un usage interne.  
  
|Nom|GUID|Description|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Retourne un `IUnknown` interface au document. En règle générale, le [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface peut être obtenue à partir de ce `IUnknown` interface.|  
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Retourne un `IUnknown` interface pour le contexte du document. En règle générale, le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface peut être obtenue à partir de ce `IUnknown` interface.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Retourne une chaîne contenant le CLSID d’une visionneuse personnalisée, généralement implémentée par un évaluateur d’expression.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Retourne un nombre 32 bits qui représente le numéro d’emplacement souhaité si cette propriété représente une adresse locale du code managé.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Retourne une chaîne contenant la signature de la variable associée à l’objet de propriété.|  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
