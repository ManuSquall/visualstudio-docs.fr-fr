---
title: IDebugExpressionEvaluator2::SetCallback | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e2ee116f7ed858121c41628515991ed4903cb15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Permet à l’évaluateur d’expression (EE) spécifier l’interface de rappel qui utilise le moteur du débogueur (DE) pour lire les paramètres de mesure.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Interface à utiliser pour le rappel de paramètres.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode fournit une interface pour le Gestionnaire de session de débogage un évaluateur d’expression peut utiliser pour lire les paramètres de mesure. Il est utile pour déboguer à distance pour lire les métriques sur le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ordinateur.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment implémenter cette méthode pour un **CEE** objet qui expose la [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interface.  
  
```cpp  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)