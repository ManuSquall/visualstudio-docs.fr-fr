---
title: IDebugQueryEngine2::GetEngineInterface | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 63f2edfe3ebd787b067c12213d783edc06e4d46c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Obtient une interface du moteur (DE) de débogage personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppUnk`  
 [out] Retourne un `IUnknown` objet représente le moteur de débogage (DE) et qui peuvent être interrogé pour toute autre interface valide associée à un DE (par exemple [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) ou [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 L’interface obtenue doit être utilisée avec précaution car l’appel des interfaces récupérées à partir de cette méthode permet de contourner le traitement du Gestionnaire de débogage de session et peut entraîner le SDM mise en route dans un état incorrect ou générer des erreurs lors du débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
