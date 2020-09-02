---
title: 'IEnumDebugCustomAttributes :: suivant | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6ce0a8199bfb279c8f8d628de0b174d7f03369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551401"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère un nombre spécifié d’attributs personnalisés dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Nombre d'éléments à récupérer. Spécifie également la taille maximale du `rgelt` tableau.  
  
 `rgelt`  
 à Tableau d’objets [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) à remplir.  
  
 `pceltFetched`  
 à Retourne le nombre d’éléments réellement retournés dans `rgelt` .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si un nombre inférieur au nombre d’éléments demandés peut être retourné ; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
