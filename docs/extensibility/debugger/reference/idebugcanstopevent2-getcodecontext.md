---
title: IDebugCanStopEvent2::GetCodeContext | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords: IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542003e3a1885a73c2d2ac7198625034930d77b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Obtient le contexte de code qui décrit l’emplacement de cet événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppCodeContext`  
 [out] Retourne le [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet qui représente l’emplacement du code en cours.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Pour la plupart des architectures d’exécution, un contexte de code peut être considéré comme une adresse dans le flux de l’exécution d’un programme, en pointant sur une instruction spécifique.  
  
 Pour obtenir le contexte de document, qui est orienté vers les lignes de code source, appelez le [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)