---
title: Concepteur d’activités CorrelationScope | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 4a46c50a888808932d071622d83b871761977259
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173197"
---
# <a name="correlationscope-activity-designer"></a>Concepteur d'activités CorrelationScope
Le **CorrelationScope** ActivityDesigner est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.CorrelationScope> activité qui fournit une gestion implicite des activités de messagerie enfants à l’aide un <xref:System.ServiceModel.Activities.CorrelationHandle> objet.  
  
## <a name="the-correlationscope-activity"></a>Activité CorrelationScope  
 La propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> contenues dans l'objet <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sont configurées pour utiliser la propriété <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de l'activité <xref:System.ServiceModel.Activities.CorrelationScope> conteneur pour effectuer la corrélation.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Utilisation du concepteur d'activités CorrelationScope  
 Le **CorrelationScope** Concepteur d’activités peut être trouvé dans le **Messaging** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet sur le côté gauche de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **CorrelationScope** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface. Cette opération crée un <xref:System.ServiceModel.Activities.CorrelationScope> activité avec une valeur par défaut **DisplayName** de CorrelationScope. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **CorrelationScope** Concepteur d’activités ou dans le **DisplayName** boîte de le **propriétés** fenêtre.  
  
 Pour spécifier le <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé par les activités de messagerie enfants, cliquez sur le bouton de sélection en regard de la **CorrelatesWith** champ **propriétés** fenêtre pour afficher le **Éditeur d’Expression**  boîte de dialogue. Cette propriété peut également être définie dans l'aire du concepteur d'activités.  
  
 Les activités dans la portée de la corrélation sont spécifiées en déposant leurs concepteurs dans les **corps** zone dans le **CorrelationScope** concepteur.  
  
### <a name="the-correlationscope-properties"></a>Propriétés de CorrelationScope  
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.CorrelationScope> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans **propriétés** fenêtre ou sur [!INCLUDE[wfd2](../includes/wfd2-md.md)] aire du concepteur, puis souvent dans les deux.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Spécifie l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour gérer les activités de messagerie enfants. Si vous ne définissez pas cette propriété, <xref:System.ServiceModel.Activities.CorrelationScope> crée automatiquement un objet <xref:System.ServiceModel.Activities.CorrelationHandle> implicite.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Spécifie les activités dans l'étendue de la corrélation.|  
  
## <a name="see-also"></a>Voir aussi  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Réception](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Envoyer](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)