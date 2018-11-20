---
title: IDebugProcess3::Execute | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13c01f9de9537e3c363f650e461a7e85b7e894ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729555"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continue ce processus en cours d’exécution à partir d’un état arrêté. N’importe quel état de l’exécution précédente (par exemple, une étape) est désactivée et le processus commence à s’exécuter à nouveau.  
  
> [!NOTE]
>  Cette méthode doit être utilisée à la place de [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread à exécuter.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsque l’utilisateur commence l’exécution à partir d’un état arrêté dans les threads d’un autre processus, cette méthode est appelée sur ce processus. Cette méthode est également appelée lorsque l’utilisateur sélectionne le **Démarrer** commande à partir de la **déboguer** menu dans l’IDE. L’implémentation de cette méthode peut être aussi simple que si vous appelez le [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) méthode sur le thread actuel dans le processus.  
  
> [!WARNING]
>  Ne pas envoyer un événement d’arrêt ou un événement (synchrone) immédiat [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors du traitement de cet appel ; sinon, le débogueur peut se bloquer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

