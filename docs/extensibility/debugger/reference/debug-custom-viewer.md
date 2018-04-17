---
title: DEBUG_CUSTOM_VIEWER | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84d8bdc7a4ea9ac59ee0956226618402b397844b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Une structure qui identifie une visionneuse personnalisée ou le type de visualiseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Membres  
 dwID  
 Un ID pour différencier plusieurs visionneuses ou implémentées par un visualiseurs `GUID`.  
  
 bstrMenuName  
 Le texte qui apparaît dans le menu déroulant.  
  
 bstrDescription  
 Description de la visionneuse personnalisée ou d’un visualiseur de type (doit être une valeur null si non utilisé).  
  
 guidLang  
 Langue de l’évaluateur d’expression en fournissant.  
  
 guidVendor  
 Fournisseur de l’évaluateur d’expression en fournissant.  
  
 bstrMetric  
 Métrique sous lequel la visionneuse personnalisée ou un visualiseur de type `CLSID` est stocké.  
  
## <a name="remarks"></a>Notes  
 Une liste de cette structure est retournée par un appel à la [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (méthode) (et, par extension, le [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)