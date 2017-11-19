---
title: DisplayKind | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a13d9146596bfc3d13cc4eea93224c5e7dceaae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="displaykind"></a>DisplayKind
Énumère les valeurs valides qui représentent les types d’informations à prendre entre une [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de l’objet et l’afficher à l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```csharp  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 DisplayKind_Value  
 Valeur du champ.  
  
 DisplayKind_Name  
 Nom du champ.  
  
 DisplayKind_Type  
 Type de champ.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)