---
title: "Classe - membres internes de tâches | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
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
ms.openlocfilehash: 21acb0a52dfde7ad565e9764e2a333a9925a2171
ms.lasthandoff: 02/22/2017

---
# <a name="task-class---internal-members"></a>Classe de tâche - membres internes
Cette rubrique décrit les membres internes de la <xref:System.Threading.Tasks.Task?displayProperty=fullName>classe qui vous aident à implémenter un débogueur personnalisé.</xref:System.Threading.Tasks.Task?displayProperty=fullName> Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Threading.Tasks.Task>rubrique de référence.</xref:System.Threading.Tasks.Task>  
  
 **Namespace :**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
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
|[SetNotificationForWaitCompletion (méthode)](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Active ou désactive le bit d’état TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[NotifyDebuggerOfWaitCompletion (méthode)](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Méthode d’espace réservé utilisé comme cible de point d’arrêt par le débogueur.|  
  
### <a name="fields"></a>Champs  
  
|Nom|Description|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Délégué qui représente le code à exécuter dans le <xref:System.Threading.Tasks.Task>objet.</xref:System.Threading.Tasks.Task>|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Stocke des propriétés supplémentaires de la <xref:System.Threading.Tasks.Task>objet.</xref:System.Threading.Tasks.Task>|  
|[m_Parent](../../extensibility/debugger/m-parent-field.md)|Le champ de stockage pour le <xref:System.Threading.Tasks.Task?displayProperty=fullName>propriété parent.</xref:System.Threading.Tasks.Task?displayProperty=fullName>|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Stocke des informations sur l’état actuel de la <xref:System.Threading.Tasks.Task>objet.</xref:System.Threading.Tasks.Task>|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objet qui représente des données qui seront utilisées par l’action.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Le champ de stockage pour le <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>propriété.</xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Le prochain identificateur disponible pour un <xref:System.Threading.Tasks.Task>objet.</xref:System.Threading.Tasks.Task>|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indique que la tâche a été annulée avant qu’elle atteint l’état en cours d’exécution, ou que la tâche a accepté le son annulation et s’est terminée sans exception.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indique que la tâche s’exécute.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indique que la tâche est terminée en raison d’une exception non gérée.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indique que la tâche terminée avec succès de l’exécution.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indique que la tâche a terminé l’exécution de son délégué et attend implicitement les tâches enfants attachées soient terminées.|  
  
## <a name="remarks"></a>Remarques  
 Les méthodes internes suivantes sont utiles pour un moteur de débogage, car ils marquent l’entrée de <xref:System.Threading.Tasks.Task>d’exécution de code :</xref:System.Threading.Tasks.Task>  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Internes de Parallel Extensions pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
