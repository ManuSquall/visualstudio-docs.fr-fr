---
description: Obtient les informations de résolution de point d’arrêt qui décrivent ce point d’arrêt.
title: 'IDebugBreakpointResolution2 :: GetResolutionInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
ms.assetid: 828cbdf6-b87d-4c45-be87-d87087b04a60
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4e0f042cc619fcd5016cf493f32ba661af4a449
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095678"
---
# <a name="idebugbreakpointresolution2getresolutioninfo"></a>IDebugBreakpointResolution2::GetResolutionInfo
Obtient les informations de résolution de point d’arrêt qui décrivent ce point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetResolutionInfo( 
   BPRESI_FIELDS       dwFields,
   BP_RESOLUTION_INFO* pBPResolutionInfo
);
```

```csharp
int GetResolutionInfo( 
   enum BPRESI_FIELDS   dwFields,
   BP_RESOLUTION_INFO[] pBPResolutionInfo
);
```

## <a name="parameters"></a>Paramètres
`dwFields`\
dans Combinaison d’indicateurs de l’énumération [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) qui détermine les champs du `pBPResolutionInfo` paramètre à remplir.

`pBPResolutionInfo`\
à Structure [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) à remplir avec des informations sur ce point d’arrêt.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple
 L’exemple suivant implémente cette méthode pour un `CDebugBreakpointResolution` objet simple qui expose l’interface [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

```
HRESULT CDebugBreakpointResolution::GetResolutionInfo(
   BPRESI_FIELDS dwFields,
   BP_RESOLUTION_INFO* pBPResolutionInfo)
{
   HRESULT hr;

   if (pBPResolutionInfo)
   {
      // Copy the specified fields of the request information from the class
      // member variable to the local BP_RESOLUTION_INFO variable.
      hr = CopyBP_RESOLUTION_INFO(m_bpResolutionInfo,
                                  *pBPResolutionInfo,
                                  dwFields);
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}

HRESULT CDebugBreakpointResolution::CopyBP_RESOLUTION_INFO(
   BP_RESOLUTION_INFO& bpResSrc,
   BP_RESOLUTION_INFO& bpResDest,
   DWORD dwFields)
{
   HRESULT hr = S_OK;

   // Start with a raw copy.
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_RESOLUTION_INFO));

   // The fields in the destination is the result of the AND of
   //  bpInfoSrc.dwFields and dwFields.
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;

   // Fill in the bp location information if the BPRESI_BPRESLOCATION
   //  flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_BPRESLOCATION))
   {
      // Switch based on the BP_TYPE.
      switch (bpResSrc.bpResLocation.bpType)
      {
         case BPT_CODE:
         {
            // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.
            bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();
            break;
         }
         case BPT_DATA:
         {
            // Copy the bstrDataExpr, bstrFunc, and bstrImage of the
            // BP_RESOLUTION_DATA structure.
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);
            bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);
            break;
         }
         default:
         {
            assert(FALSE);
            // Clear the BPRESI_BPRESLOCATION flag in the BPRESI_FIELDS
            // of the destination BP_RESOLUTION_INFO.
            ClearFlag(bpResDest.dwFields, BPRESI_BPRESLOCATION);
            break;
         }
      }
   }
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_PROGRAM))
   {
      bpResDest.pProgram->AddRef();
   }
   // AddRef the IDebugThread2 if the BPRESI_THREAD flag is set in BPRESI_FIELDS.
   if (IsFlagSet(bpResDest.dwFields, BPRESI_THREAD))
   {
      bpResDest.pThread->AddRef();
   }

   return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
