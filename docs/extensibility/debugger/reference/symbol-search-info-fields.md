---
title: SYMBOL_SEARCH_INFO_FIELDS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c69f21c72e8816d9ddf6eb5b88cf7798bc7d1f4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127547"
---
# <a name="symbolsearchinfofields"></a>SYMBOL_SEARCH_INFO_FIELDS
Spécifie le type d’informations de symbole à récupérer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## <a name="members"></a>Membres  
 SSIF_NONE  
 Ne spécifie aucun indicateur  
  
 SSIF_VERBOSE_SEARCH_INFO  
 Retourne que tous les chemins d’accès utilisés pour la recherche de symboles de recherche  
  
## <a name="remarks"></a>Notes  
 Ces indicateurs sont passés en tant que paramètre à la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) retourné de la méthode pour déterminer la quantité d’informations.  
  
> [!NOTE]
>  Actuellement, uniquement `SSIF_VERBOSE_SEARCH_INFO` est pris en charge, et il doit être spécifié en tant que le `dwFlags` paramètre `IDebugModule3::GetSymbolInfo`. Toutes les autres valeurs renvoient une erreur.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)