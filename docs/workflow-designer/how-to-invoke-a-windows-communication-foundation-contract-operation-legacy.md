---
title: "Proc&#233;dure&#160;: appeler une op&#233;ration de contrat Windows Communication Foundation (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Proc&#233;dure&#160;: appeler une op&#233;ration de contrat Windows Communication Foundation (h&#233;rit&#233;e)
Cette rubrique décrit comment appeler une opération de contrat [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Après avoir fait glisser une activité **SendActivity** de la boîte à outils vers l'aire de conception du workflow, vous devez importer un contrat existant et déterminer l'opération qui sera appelée à partir de cette activité **SendActivity**.Pour sélectionner votre contrat et les opérations correspondantes, utilisez la [Choisir une opération, boîte de dialogue \(héritée\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Par ailleurs, si vous utilisez un fichier de configuration avec votre service, vous devrez indiquer un jeton <xref:System.Workflow.Activities.ChannelToken>.<xref:System.Workflow.Activities.ChannelToken> identifie la configuration de point de terminaison qui sera utilisée par l'activité d'envoi pour se connecter au service de workflow.  
  
### Appel d'une opération de contrat WCF à partir d'une activité SendActivity  
  
1.  Double\-cliquez sur l'activité **SendActivity** dans le concepteur ou cliquez sur les points de suspension jouxtant la propriété **ServiceOperationInfo** dans le volet **Propriétés**.  
  
2.  Lorsque la boîte de dialogue **Choisir une opération** s'ouvre, cliquez sur **Importer** dans l'angle supérieur droit de la boîte de dialogue.  
  
     La [Rechercher et sélectionner un type .NET, boîte de dialogue \(héritée\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s'ouvre.  
  
3.  Recherchez un assembly ou un projet contenant le contrat souhaité.  
  
4.  Sélectionnez le contrat puis cliquez sur **OK**.  
  
5.  Sous **Opérations disponibles**, sélectionnez l'opération à appeler et cliquez sur **OK**.  
  
### Indication d'un jeton de canal  
  
1.  Sélectionnez l'activité <xref:System.Workflow.Activities.SendActivity> dans le concepteur.  
  
2.  Dans le volet **Propriétés**, indiquez un nom pour le <xref:System.Workflow.Activities.ChannelToken>.Ce nom identifie uniquement le jeton de canal.  
  
3.  Développez le nœud du jeton de canal et indiquez un nom pour le point de terminaison client à utiliser dans le champ <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>.La configuration de point de terminaison correspondant au même nom dans le fichier de configuration sera utilisée pour configurer le canal.  
  
4.  Créez la configuration de point de terminaison dans le fichier de configuration, s'il n'existe pas déjà.Pour plus d'informations sur la configuration du client, consultez [Vue d'ensemble d'un client WCF](../Topic/WCF%20Client%20Overview.md).  
  
## Voir aussi  
 [Choisir une opération, boîte de dialogue \(héritée\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procédure : implémenter une opération de contrat WCF \(héritée\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)