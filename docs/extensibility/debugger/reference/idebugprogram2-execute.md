---
title: IDebugProgram2::Execute | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7f4e26a5c892e1c796a2b6e2f9371898db21f68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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