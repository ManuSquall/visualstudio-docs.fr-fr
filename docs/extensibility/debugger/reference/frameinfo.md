---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "Structure FRAMEINFO"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit un frame de pile.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## Membres  
 m\_dwValidFields  
 Une combinaison des indicateurs d'énumération de [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) qui spécifie quels champs sont remplis.  
  
 m\_bstrFuncName  
 Le nom de la fonction associé au frame de pile.  
  
 m\_bstrReturnType  
 Le type de retour associé au frame de pile.  
  
 m\_bstrArgs  
 Les arguments de la fonction associée au frame de pile.  
  
 m\_bstrLanguage  
 le langage dans lequel la fonction est implémentée.  
  
 m\_bstrModule  
 Le nom du module associé au frame de pile.  
  
 m\_addrMin  
 l'adresse physique minimum de pile.  
  
 m\_addrMAX  
 L'adresse physique maximale de pile.  
  
 m\_pFrame  
 l'objet d' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui représente ce frame de pile.  
  
 m\_pFrame  
 l'objet d' [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui représente le module qui contient ce frame de pile.  
  
 m\_fHasDebugInfo  
 Différente de zéro \(`TRUE`\) si les informations de débogage existent dans le frame donné.  
  
 m\_fHasDebugInfo  
 Différente de zéro \(`TRUE`\) si le frame de pile est associé au code qui n'est plus valide.  
  
 m\_fHasDebugInfo  
 Différente de zéro \(`TRUE`\) si le frame de pile est annotée par le gestionnaire de débogage de \(SDM\) session.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) à accomplir.  Cette structure est également contenue dans une liste contenue dans l'interface d' [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) qui, à son tour, est retournée à partir d'un appel à la méthode d' [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)