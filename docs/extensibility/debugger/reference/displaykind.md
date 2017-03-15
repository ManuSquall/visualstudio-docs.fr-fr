---
title: "DisplayKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayKind (énumération)"
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# DisplayKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Énumère les valeurs valides qui représentent les types d'informations pour prendre d'un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et d'afficher à l'utilisateur.  
  
## Syntaxe  
  
```cpp#  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```c#  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### Paramètres  
 DisplayKind\_Value  
 valeur du champ.  
  
 DisplayKind\_Name  
 nom du champ.  
  
 DisplayKind\_Type  
 type de champ.  
  
## Configuration requise  
 en\-tête : Ee.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)