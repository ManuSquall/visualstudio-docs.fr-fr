---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8c1b438cd2fa2721e81f055695e5836c26d12
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952685"
---
# <a name="contextinfo"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Un contexte de la mémoire ou d’un contexte de code décrite par cette structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Membres  
 dwFields  
 Une combinaison d’indicateurs d’il [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) énumération qui spécifie quels champs sont renseignés<strong>.</strong>  
  
 bstrModuleUrl  
 Le nom du module où se trouve le contexte.  
  
 bstrFunction  
 Le nom de la fonction où se trouve le contexte.  
  
 posFunctionOffset  
 Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure qui identifie l’offset de ligne et colonne de la fonction associée au contexte de code.  
  
 bstrAddress  
 L’adresse dans le code où se trouve le contexte donné.  
  
 bstrAddressOffset  
 Le décalage de l’adresse dans le code où se trouve le contexte donné.  
  
 bstrAddressAbsolute  
 L’adresse absolue en mémoire où se trouve le contexte donné.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée à partir d’un appel à la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) (méthode).  
  
 En règle générale pour cette structure est à l’appui d’un **mémoire** fenêtre de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
