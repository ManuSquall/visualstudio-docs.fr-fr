---
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6134c10f30d66011dca5e40c28b6cbe6a7c94ed
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430554"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continue de s’exécuter ce programme à partir d’un état arrêté. N’importe quel état de l’exécution précédente (par exemple, une étape) est désactivée, et le programme commence à s’exécuter à nouveau.  
  
> [!NOTE]
> Cette méthode est dépréciée. Utilisez le [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Lorsque l’utilisateur commence l’exécution à partir d’un état arrêté dans les threads d’un autre programme, cette méthode est appelée sur ce programme. Cette méthode est également appelée lorsque l’utilisateur sélectionne le **Démarrer** commande à partir de la **déboguer** menu dans l’IDE. L’implémentation de cette méthode peut être aussi simple que si vous appelez le [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) méthode sur le thread actuel dans le programme.  
  
> [!WARNING]
> Ne pas envoyer un événement d’arrêt ou un événement (synchrone) immédiat [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors du traitement de cet appel ; sinon, le débogueur peut se bloquer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
