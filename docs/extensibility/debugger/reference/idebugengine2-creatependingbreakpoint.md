---
title: IDebugEngine2::CreatePendingBreakpoint | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords: IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdc73a2245390ec04cc3adc2b3a4ac4f5ced3f51
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crée un point d’arrêt en attente dans le moteur de débogage (DE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBPRequest`  
 [in] Un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) objet qui décrit le point d’arrêt en attente à créer.  
  
 `ppPendingBP`  
 [out] Retourne un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objet qui représente le point d’arrêt en attente.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne généralement `E_FAIL` si le `pBPRequest` paramètre ne correspond pas à n’importe quel langage pris en charge par le DE if le `pBPRequest` paramètre est non valide ou incomplète.  
  
## <a name="remarks"></a>Remarques  
 Un point d’arrêt en attente est essentiellement une collection de toutes les informations nécessaires pour lier un point d’arrêt au code. Le point d’arrêt en attente retournée par cette méthode n’est pas lié au code jusqu'à ce que le [lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) méthode est appelée.  
  
 Pour chaque point d’arrêt en attente de l’utilisateur définit, le Gestionnaire de session de débogage (SDM) appelle cette méthode dans chaque DE attaché. C’est à la DE vérifier que le point d’arrêt est valide pour les programmes en cours d’exécution dans ce DE.  
  
 Lorsque l’utilisateur définit un point d’arrêt sur une ligne de code, la D’est gratuite lier le point d’arrêt à la ligne la plus proche dans le document qui correspond à ce code. Cela permet à l’utilisateur de définir un point d’arrêt sur la première ligne d’une instruction sur plusieurs lignes, mais la lier à la dernière ligne (où tout le code est attribué dans les informations de débogage).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour une simple `CProgram` objet. Implémentation de la DE la `IDebugEngine2::CreatePendingBreakpoint` puis Impossible pour transférer tous les appels à cette implémentation de la méthode dans chaque programme.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)