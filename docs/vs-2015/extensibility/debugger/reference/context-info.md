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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179943"
---
# <a name="context_info"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette structure décrit un contexte de mémoire ou un contexte de code.  
  
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
 Combinaison d’indicateurs de l’énumération [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) qui spécifie les champs à remplir<strong>.</strong>  
  
 bstrModuleUrl  
 Nom du module dans lequel se trouve le contexte.  
  
 bstrFunction  
 Nom de la fonction dans laquelle se trouve le contexte.  
  
 posFunctionOffset  
 Structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui identifie le décalage de ligne et de colonne de la fonction associée au contexte de code.  
  
 bstrAddress  
 Adresse dans le code où se trouve le contexte donné.  
  
 bstrAddressOffset  
 Offset de l’adresse dans le code où se trouve le contexte donné.  
  
 bstrAddressAbsolute  
 Adresse absolue dans la mémoire où se trouve le contexte donné.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée à partir d’un appel à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .  
  
 Une utilisation classique de cette structure est la prise en charge d’une fenêtre de débogage de la **mémoire** .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
