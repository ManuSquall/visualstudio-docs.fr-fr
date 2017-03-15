---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "Fonction de rappel OPTNAMECHANGEPFN"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il s'agit d'une fonction de rappel spécifiée dans un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) \(à l'aide d'option `SCC_OPT_NAMECHANGEPFN`\) et est utilisé pour communiquer les modifications de nom effectuées par le contrôle de code source du plug\-in à l'IDE.  
  
## Signature  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## Paramètres  
 pvCallerData  
 \[in\] Valeur de l'utilisateur spécifié dans un appel précédent à la [SccSetOption](../extensibility/sccsetoption-function.md) \(à l'aide d'option `SCC_OPT_USERDATA`\).  
  
 pszOldName  
 \[in\] Le nom du fichier d'origine.  
  
 pszNewName  
 \[in\] Le nom du fichier a été renommé.  
  
## Valeur de retour  
 Aucun  
  
## Notes  
 Si un fichier est renommé pendant une opération de contrôle de code source, le plug\-in de contrôle de code source peut avertir l'IDE sur le changement de nom à ce rappel.  
  
 Si l'IDE ne prend pas en charge ce rappel, elle n'appelle pas la [SccSetOption](../extensibility/sccsetoption-function.md) pour le spécifier. Si le plug\-in ne prend pas en charge ce rappel, elle retournera `SCC_E_OPNOTSUPPORTED` à partir de la `SccSetOption` lorsque l'IDE tente de définir le rappel de fonction.  
  
## Voir aussi  
 [Fonctions de rappel implémentées par l'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)