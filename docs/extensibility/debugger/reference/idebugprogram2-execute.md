---
title: IDebugProgram2::Execute | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Execute
helpviewer_keywords: IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2e53f13aea93de8f39c5802dd2a12598ad938f64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continue de s’exécuter ce programme à partir d’un état arrêté. N’importe quel état précédent de l’exécution (par exemple, une étape) est désactivée, et le programme commence à s’exécuter à nouveau.  
  
> [!NOTE]
>  Cette méthode est déconseillée. Utilisez le [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsque l’utilisateur commence l’exécution à partir d’un état d’arrêt dans les threads d’un autre programme, cette méthode est appelée sur ce programme. Cette méthode est également appelée lorsque l’utilisateur sélectionne le **Démarrer** commande à partir de la **déboguer** menu dans l’IDE. L’implémentation de cette méthode peut être aussi simple que d’appeler le [reprise](../../../extensibility/debugger/reference/idebugthread2-resume.md) méthode sur le thread actuel dans le programme.  
  
> [!WARNING]
>  Ne pas envoyer un événement d’arrêt ou un événement (synchrone) immédiat [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors du traitement de cet appel ; sinon, le débogueur peut se bloquer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)