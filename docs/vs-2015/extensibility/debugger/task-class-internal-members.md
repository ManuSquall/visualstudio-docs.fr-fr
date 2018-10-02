---
title: Classe de tâche - membres internes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a110e81f149fc04c973fcfe0160873a0bf633f72
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496360"
---
# <a name="task-class---internal-members"></a>Classe de tâche - Membres internes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [classe de tâche - membres internes](https://docs.microsoft.com/visualstudio/extensibility/debugger/task-class-internal-members).  
  
Cette rubrique décrit les membres internes de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe qui vous aident à implémenter un débogueur personnalisé. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Threading.Tasks.Task> rubrique de référence.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Définit ou efface le bit d’état TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Méthode NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Méthode d’espace réservé utilisée comme cible de point d’arrêt par le débogueur.|  
  
### <a name="fields"></a>Champs  
  
|Name|Description|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Délégué qui représente le code à exécuter dans le <xref:System.Threading.Tasks.Task> objet.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Stocke des propriétés supplémentaires de la <xref:System.Threading.Tasks.Task> objet.|  
|[m_Parent](../../extensibility/debugger/m-parent-field.md)|Le champ de stockage pour le <xref:System.Threading.Tasks.Task?displayProperty=fullName> propriété parente.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Stocke des informations sur l’état actuel de la <xref:System.Threading.Tasks.Task> objet.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objet qui représente les données qui seront utilisées par l’action.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Le champ de stockage pour le <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> propriété.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|L’identificateur suivant disponible pour un <xref:System.Threading.Tasks.Task> objet.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indique que la tâche a été annulée avant d’atteindre l’état en cours d’exécution, ou que la tâche a accepté sa l’annulation et s’est terminée sans exception.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indique que la tâche est en cours d’exécution.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indique que la tâche est terminée en raison d’une exception non gérée.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indique que la tâche a réussi l’exécution.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indique que la tâche a terminé l’exécution de son délégué et attend implicitement les tâches enfants attachées soient terminées.|  
  
## <a name="remarks"></a>Notes  
 Les méthodes internes suivantes sont utiles pour un moteur de débogage, car ils servent à indiquer l’entrée de <xref:System.Threading.Tasks.Task> d’exécution de code :  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Valeurs internes d’extension parallèle pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

