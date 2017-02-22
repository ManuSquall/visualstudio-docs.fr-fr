---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "EncUnavailableReason (énumération)"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` représente les raisons pour lesquelles **Modifier & Continuer** est pas disponible.  
  
## Syntaxe  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### Paramètres  
 ENCUN\_NONE  
 Aucune raison spécifique pour laquelle la modification et Continue est pas disponible.  
  
 ENCUN\_INTEROP  
 La modification et Continue est pas disponible pendant un appel d'interopérabilité.  
  
 ENCUN\_SQLCLR  
 La modification et Continue est pas disponible pendant un appel de procédure SQL qui utilise le common langage runtime \(CLR\).  
  
 ENCUN\_MINIDUMP  
 La modification et Continue est pas disponible pendant le traitement d'un mini\-dump.  
  
 ENCUN\_EMBEDDED  
 La modification et Continue est pas disponible en traitant du code incorporé.  
  
 ENCUN\_ATTACH  
 La modification et Continue est pas disponible car la session a été rattachée, non lancé par, le débogueur.  
  
 ENCUN\_WIN64  
 La modification et Continue est pas disponible pendant le traitement du code 64 bits de windows.  
  
## Notes  
 Cette énumération est destiné à un usage interne uniquement par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  Les méthodes d' [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) et d' [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) comme implémentées par un fournisseur personnalisé de port doivent toujours retourner `E_NOTIMPL`.  
  
## Configuration requise  
 en\-tête : msdbg.idl  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)