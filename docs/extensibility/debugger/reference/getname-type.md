---
title: "GETNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "Énumération de GETNAME_TYPE"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type de nom de fichier pour récupérer.  
  
## Syntaxe  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## Membres  
 GN\_NAME  
 spécifie un nom convivial du document ou du contexte.  
  
 GN\_FILENAME  
 Spécifie le chemin d'accès complet du document ou du contexte.  
  
 GN\_BASENAME  
 Spécifie un nom de fichier de base au lieu d'un chemin d'accès complet du document ou du contexte.  
  
 GN\_MONIKERNAME  
 Spécifie un nom unique du document ou du contexte sous la forme d'un moniker.  
  
 GN\_URL  
 spécifie un nom d'URL du document ou du contexte.  
  
 GN\_TITLE  
 Spécifie un titre du document, le cas échéant.  
  
 GN\_STARTPAGEURL  
 Obtient l'URL de démarrage de page pour les processus.  
  
## Notes  
 Ces valeurs sont passées en tant que paramètres aux méthodes d' [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), d' [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), et d' [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) pour spécifier le type nom à retourner.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)