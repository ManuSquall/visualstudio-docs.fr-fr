---
title: 'IDebugProperty2 :: GetPropertyInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a6d4c2fd943ddef0b4459460be1f67550e53d84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146271"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui décrit une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFields`  
 dans Combinaison de valeurs de l’énumération [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) qui spécifie les champs à remplir dans la `pPropertyInfo` structure.  
  
 `nRadix`  
 dans Base à utiliser pour mettre en forme les informations numériques.  
  
 `dwTimeout`  
 dans Spécifie la durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
 `rgpArgs`  
 [in, out] Réservé à une utilisation ultérieure ; défini sur une valeur null.  
  
 `dwArgCount`  
 dans Réservé à une utilisation ultérieure ; défini à zéro.  
  
 `pPropertyInfo`  
 à Structure [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) qui est remplie avec la description de la propriété.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
