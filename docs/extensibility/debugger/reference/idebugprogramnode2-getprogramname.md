---
title: "IDebugProgramNode2::GetProgramName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetProgramName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetProgramName"
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom du programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```c#  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### Paramètres  
 `pbstrProgramName`  
 \[out\]  Retourne le nom du programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le nom d'un programme n'est pas le même que le chemin d'accès au programme, ainsi que le nom du programme puisse faire partie de ce chemin d'accès.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CProgram` qui implémente l'interface d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .  La fonction d' `MakeBstr` alloue une copie de la chaîne spécifiée comme un BSTR.  
  
```cpp#  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)