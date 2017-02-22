---
title: "PORT_SUPPLIER_DESCRIPTION_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Énumération de PORT_SUPPLIER_DESCRIPTION_FLAGS"
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PORT_SUPPLIER_DESCRIPTION_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit les métadonnées qui peuvent être récupérées à propos d'un fournisseur de port.  
  
## Syntaxe  
  
```cpp#  
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;  
```  
  
```c#  
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
```  
  
## termes  
 PSDFLAG\_SHOW\_WARNING\_ICON  
 Si sélectionnée, l'icône d'avertissement s'affiche dans l'interface utilisateur.  
  
## Notes  
 cette énumération est retournée par la méthode d' [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) .  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)