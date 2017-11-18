---
title: "Comment : appeler une opération de contrat Windows Communication Foundation (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51b20275f63b47d607679e04ff061cf77b0d9f90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : appeler une opération de contrat Windows Communication Foundation (héritée)
Cette rubrique décrit comment appeler une opération de contrat [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Après avoir fait glisser un **SendActivity** activité à partir de la boîte à outils vers l’aire de conception de workflow, vous devez importer un contrat existant et déterminer quelle opération doit être appelée à partir de ce **SendActivity** activité. Vous sélectionnez votre contrat et ses opérations via le [opération boîte de dialogue Choisir (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Par ailleurs, si vous utilisez un fichier de configuration avec votre service, vous devrez indiquer un jeton <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifie la configuration de point de terminaison qui sera utilisée par l'activité d'envoi pour se connecter au service de workflow.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Appel d'une opération de contrat WCF à partir d'une activité SendActivity  
  
1.  Double-cliquez sur le **SendActivity** activité dans le concepteur ou cliquez sur le bouton de sélection en regard du **ServiceOperationInfo** propriété dans le **propriétés** volet.  
  
2.  Lorsque le **choisir une opération** boîte de dialogue s’ouvre, cliquez sur **importation** dans le coin supérieur droit de la boîte de dialogue.  
  
     Le [rechercher et sélectionner une boîte de dialogue du Type .NET (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s’ouvre.  
  
3.  Recherchez un assembly ou un projet contenant le contrat souhaité.  
  
4.  Sélectionnez le contrat, puis cliquez sur **OK**.  
  
5.  Sous **opérations disponibles**, sélectionnez l’opération que vous souhaitez appeler et cliquez sur **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Indication d'un jeton de canal  
  
1.  Sélectionnez l'activité <xref:System.Workflow.Activities.SendActivity> dans le concepteur.  
  
2.  Dans le **propriétés** volet, spécifiez un nom pour le <xref:System.Workflow.Activities.ChannelToken>. Ce nom identifie uniquement le jeton de canal.  
  
3.  Développez le nœud du jeton de canal et indiquez un nom pour le point de terminaison client à utiliser dans le champ <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuration de point de terminaison correspondant au même nom dans le fichier de configuration sera utilisée pour configurer le canal.  
  
4.  Créez la configuration de point de terminaison dans le fichier de configuration, s'il n'existe pas déjà. Pour plus d’informations sur la configuration de votre client, consultez [vue d’ensemble du Client WCF](/dotnet/framework/wcf/wcf-client-overview).  
  
## <a name="see-also"></a>Voir aussi  
 [Choisissez l’opération, boîte de dialogue (héritée)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)