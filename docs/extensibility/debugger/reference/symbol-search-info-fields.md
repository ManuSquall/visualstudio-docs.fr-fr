---
title: "SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SYMBOL_SEARCH_INFO_FIELDS"
helpviewer_keywords: 
  - "Énumération de SYMBOL_SEARCH_INFO_FIELDS"
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SYMBOL_SEARCH_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type d'informations de symbole d'extraire.  
  
## Syntaxe  
  
```cpp#  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```c#  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## Membres  
 SSIF\_NONE  
 N'indique pas de balise  
  
 SSIF\_VERBOSE\_SEARCH\_INFORMATION  
 Retourne tous les chemins de recherche utilisés pour rechercher des symboles  
  
## Notes  
 Ces indicateurs sont passées en tant que paramètre à la méthode de [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) pour déterminer la quantité d'informations retournées.  
  
> [!NOTE]
>  Actuellement, seuls `SSIF_VERBOSE_SEARCH_INFO` est pris en charge, et il doit être spécifié comme paramètre d' `dwFlags` à `IDebugModule3::GetSymbolInfo`.  Toutes les autres valeurs retournent une erreur.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)