---
title: "IDebugProgram2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugProgram2::GetDebugProperty"
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient les propriétés du programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### Paramètres  
 `ppProperty`  
 \[out\]  Retourne un objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente les propriétés du programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 les propriétés retournées par cette méthode sont spécifiques au programme.  Si le programme doit retourner plusieurs propriétés, l'objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) retourné par cette méthode est un conteneur de propriétés supplémentaires et d'appeler la méthode d' [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) retourne une liste de toutes les propriétés.  
  
 Un programme peut exposer n'importe quel nombre et le type de propriétés supplémentaires qui peuvent être décrits via l'interface d' `IDebugProperty2` .  L'IDE peut afficher des propriétés supplémentaires de programme via une interface utilisateur générique de l'Explorateur de propriétés.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)