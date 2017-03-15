---
title: "IDebugClassField::DoesInterfaceExist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::DoesInterfaceExist"
helpviewer_keywords: 
  - "IDebugClassField::DoesInterfaceExist (méthode)"
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si une interface spécifique est définie dans la classe.  
  
## Syntaxe  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```c#  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### Paramètres  
 `pszInterfaceName`  
 \[in\]  Chaîne contenant le nom de l'interface pour rechercher.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK, retourne S\_FALSE si l'interface n'existe pas ; sinon, retourne un code d'erreur.  
  
## Notes  
 cette méthode en effet obtient une énumération de toutes les interfaces et recherche la liste pour une interface correspondante.  
  
## Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)