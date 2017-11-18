---
title: "Concepteurs d’activités de messagerie | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2aa2383326682dcedbb0888f5b55d34e3894327c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="messaging-activity-designers"></a>Concepteurs d'activités de messagerie
Les concepteurs d'activités de messagerie permettent de créer et configurer des activités de messagerie qui envoient et reçoivent des messages [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] à partir d'une application [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. Le [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] introduit cinq activités de messagerie et [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fournit deux nouveaux concepteurs de modèles qui vous permettent de gérer la messagerie dans un workflow. Les rubriques contenues dans cette section et répertoriées dans le tableau suivant fournissent des conseils sur la façon d'utiliser les concepteurs d'activités et de modèles [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Activité de message|Description|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Crée et configure une activité <xref:System.ServiceModel.Activities.CorrelationScope> qui fournit une gestion implicite des activités de messagerie enfants avec un objet <xref:System.ServiceModel.Activities.CorrelationHandle>.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Crée et configure une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> utilisée pour initialiser la corrélation sans envoyer ou recevoir de message.|  
|[Réception](../workflow-designer/receive-activity-designer.md)|Crée et configure une activité <xref:System.ServiceModel.Activities.Receive> qui reçoit un message d'un service.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Crée une paire préconfigurée d'activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> dans une activité <xref:System.Activities.Statements.Sequence>.|  
|[Envoyer](../workflow-designer/send-activity-designer.md)|Crée et configure une activité <xref:System.ServiceModel.Activities.Send> qui envoie un message à un service.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Crée une paire préconfigurée d'activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> dans une activité <xref:System.Activities.Statements.Sequence>.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Crée et configure une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> qui active le flux de transactions dans un workflow.|  
  
## <a name="reference"></a>Référence  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour les autres types de concepteurs d'activités, consultez les rubriques suivantes.  
  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)  
  
 [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md)  
  
 [Organigramme](../workflow-designer/flowchart-activity-designers.md)  
  
 [Runtime](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [Transaction](../workflow-designer/transaction-activity-designers.md)  
  
 [Collection](../workflow-designer/collection-activity-designers.md)  
  
 [Gestion des erreurs](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Ressources externes  
 [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md)