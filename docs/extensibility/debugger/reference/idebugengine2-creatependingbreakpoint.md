---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée un point d'arrêt en attente dans le moteur de débogage \(DE\).  
  
## Syntaxe  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### Paramètres  
 `pBPRequest`  
 \[in\]  Un objet d' [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) qui décrit le point d'arrêt en attente à créer.  
  
 `ppPendingBP`  
 \[out\]  Retourne un objet d' [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le point d'arrêt en attente.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne généralement `E_FAIL` si le paramètre d' `pBPRequest` ne correspond pas à un langage pris en charge par le De la définition du paramètre d' `pBPRequest` est valide ou incomplet.  
  
## Notes  
 Un point d'arrêt en attente est une collection de toutes les informations nécessaires pour lier un point d'arrêt au code.  Le point d'arrêt en attente retourné par cette méthode n'est pas lié au code jusqu'à ce que la méthode d' [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) soit appelée.  
  
 Pour chaque point d'arrêt en attente des ensembles d'utilisateur, le gestionnaire de débogage de \(SDM\) session appelle cette méthode dans chaque DE attaché.  Ils appartiennent au De à vérifier que le point d'arrêt est valide pour les programmes s'exécutant dans le DE.  
  
 Lorsque l'utilisateur définit un point d'arrêt sur une ligne de code, le du est libre pour lier le point d'arrêt à la ligne la plus proche le document qui correspond à ce code.  Cela permet à l'utilisateur place un point d'arrêt sur la première ligne d'une instruction sur plusieurs lignes, mais les liens sur la dernière ligne \(où tout le code est attribué dans les informations de débogage\).  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CProgram` .  L'implémentation Du D ' `IDebugEngine2::CreatePendingBreakpoint` pourrait ensuite transférer tous les appels à cette implémentation de la méthode dans chaque programme.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)