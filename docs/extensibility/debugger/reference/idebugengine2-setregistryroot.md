---
title: "IDebugEngine2::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la racine de Registre pour le moteur de débogage \(DE\).  
  
## Syntaxe  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### Paramètres  
 `pszRegistryRoot`  
 \[in\]  La racine de Registre à utiliser.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode permet à [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pour spécifier une autre racine de Registre que le De doit utiliser pour obtenir des paramètres du Registre ; par exemple, « HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp ».  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)