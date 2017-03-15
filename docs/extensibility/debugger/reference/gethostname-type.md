---
title: "GETHOSTNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETHOSTNAME_TYPE"
helpviewer_keywords: 
  - "Énumération de GETHOSTNAME_TYPE"
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GETHOSTNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type de nom d'hôte.  
  
## Syntaxe  
  
```cpp#  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```c#  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## Membres  
 GHN\_FRIENDLY\_NAME  
 spécifie un nom convivial de l'hôte.  
  
 GHN\_FILE\_NAME  
 spécifie un nom de fichier de l'hôte.  
  
## Notes  
 Ces valeurs sont passées en tant qu'argument à la méthode d' [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) et récupérer le nom d'hôte dans différents formats.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)