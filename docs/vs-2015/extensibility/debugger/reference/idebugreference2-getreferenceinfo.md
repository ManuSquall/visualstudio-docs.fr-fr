---
title: IDebugReference2::GetReferenceInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77cccb562db79d9f6a53113bda0c4434e19c6813
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950512"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure qui décrit une référence. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFields`  
 [in] Une combinaison d’indicateurs de la [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) énumération qui déterminent les champs à compléter le [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure.  
  
 `nRadix`  
 [in] La base à utiliser dans toutes les informations numériques de mise en forme.  
  
 `dwTimeout`  
 [in] Durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
 `rgpArgs`  
 [in] Un tableau de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objets. Réservé pour une utilisation ultérieure ; la valeur est une valeur null.  
  
 `dwArgCount`  
 [in] Le nombre d’arguments de référence dans le `rgpArgs` tableau. Réservé pour une utilisation ultérieure ; la valeur 0.  
  
 `pReferenceInfo`  
 [out] Un [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure est remplie avec une description de la propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
