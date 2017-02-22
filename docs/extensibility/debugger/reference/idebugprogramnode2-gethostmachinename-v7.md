---
title: "IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetHostMachineName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostMachineName_V7"
  - "IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName"
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

DÉCONSEILLÉ.  NE SUR UTILISEZ NOT.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```c#  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### Paramètres  
 `pbstrHostMachineName`  
 \[out\]  Retourne le nom de l'ordinateur dans lequel le programme s'exécute.  
  
## Valeur de retour  
 Une implémentation doit toujours retourner `E_NOTIMPL`.  
  
## Notes  
  
> [!WARNING]
>  À partir de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], cette méthode est plus utilisée et ne doivent toujours retourner `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)