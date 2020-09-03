---
title: 'IDebugReference2 :: GetReferenceInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155825"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui décrit une référence. Réservé à un usage ultérieur.  
  
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
 dans Combinaison d’indicateurs de l’énumération [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) qui déterminent les champs à remplir dans la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
 `nRadix`  
 dans Base à utiliser pour mettre en forme les informations numériques.  
  
 `dwTimeout`  
 dans Durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
 `rgpArgs`  
 dans Tableau d’objets [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Réservé à une utilisation ultérieure ; défini sur une valeur null.  
  
 `dwArgCount`  
 dans Nombre d’arguments de référence dans le `rgpArgs` tableau. Réservé à une utilisation ultérieure ; défini sur 0.  
  
 `pReferenceInfo`  
 à Structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui est remplie avec une description de la propriété.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
