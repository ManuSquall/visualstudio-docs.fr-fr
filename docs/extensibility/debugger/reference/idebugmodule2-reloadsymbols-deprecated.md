---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "IDebugModule2::ReloadSymbols (méthode)"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

OBSOLÈTE.  NE SUR UTILISEZ NOT.  recharge les symboles pour ce module.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### Paramètres  
 `pszUrlToSymbols`  
 \[in\]  le chemin d'accès au magasin de symboles.  
  
 `pbstrDebugMessage`  
 \[out\]  Retourne un message d'information, tel qu'un rapport ou un message d'erreur, affichés à droite du nom du module dans la fenêtre modules.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Un moteur de débogage doit toujours retourner `E_FAIL`.  
  
## Notes  
 Cette méthode n'est plus prise en charge.  Implémentez la méthode d' [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md) à la place.  
  
## Voir aussi  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)