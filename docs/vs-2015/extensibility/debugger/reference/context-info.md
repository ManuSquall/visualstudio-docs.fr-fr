---
title: CONTEXT_INFO | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a915458c00e75f6acb62434e184170420d15aad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508668"
---
# <a name="contextinfo"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CONTEXT_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/context-info).  
  
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
 Une combinaison d’indicateurs d’il [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) énumération qui spécifie quels champs sont renseignés **.**  
  
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
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

