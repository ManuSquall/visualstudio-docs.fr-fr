---
title: "Proc&#233;dure&#160;: impl&#233;menter une op&#233;ration de contrat Windows Communication Foundation (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Proc&#233;dure&#160;: impl&#233;menter une op&#233;ration de contrat Windows Communication Foundation (h&#233;rit&#233;e)
Cette rubrique décrit comment implémenter une opération de contrat [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Après avoir fait glisser une activité **ReceiveActivity** de la boîte à outils vers l'aire de conception de workflow, vous pouvez soit créer un contrat [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)], soit importer un contrat existant et y implémenter les opérations.Pour sélectionner et\/ou créer un contrat et les opérations correspondantes, utilisez la [Choisir une opération, boîte de dialogue \(héritée\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### Implémentation d'une opération de contrat WCF  
  
1.  Double\-cliquez sur l'activité **ReceiveActivity** dans le concepteur ou cliquez sur les points de suspension jouxtant la propriété **ServiceOperationInfo** dans le volet **Propriétés**.  
  
2.  Effectuez l'une des opérations suivantes :  
  
    -   Cliquez sur **Ajouter un contrat** dans l'angle supérieur droit de la boîte de dialogue.Cette opération créera un nouveau contrat [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] ainsi que les opérations correspondantes.  
  
         ou  
  
    -   Cliquez sur **Importer** dans l'angle supérieur droit de la boîte de dialogue.La [Rechercher et sélectionner un type .NET, boîte de dialogue \(héritée\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s'ouvre.Recherchez un assembly ou un projet contenant le contrat souhaité.Sélectionnez le contrat puis cliquez sur **OK**.  
  
     Une fois un contrat créé ou importé, vous pouvez y ajouter de nouvelles opérations.Pour ce faire, sélectionnez le contrat et cliquez sur **Ajouter une opération** dans l'angle supérieur droit de la boîte de dialogue.Lorsque vous avez terminé l'ajout d'opérations, passez à étape 3.  
  
3.  Sélectionnez l'opération à associer à l'activité **ReceiveActivity**.Vous pouvez manipuler la définition de l'opération en modifiant son nom, ses paramètres, ses propriétés et ses paramètres d'autorisation.  
  
     Pour modifier le nom, indiquez un nouveau nom dans la zone de texte **Nom de l'opération**.  
  
     Cliquez sur l'onglet **Paramètres** pour accéder aux paramètres de l'opération.Vous pouvez modifier le nom, le type ou la direction d'un paramètre ; il est également possible d'ajouter ou de supprimer des paramètres de l'opération.  
  
     Cliquez sur l'onglet **Propriétés** pour accéder au niveau de protection de l'opération ainsi qu'à la fonctionnalité d'échange de messages prise en charge.  
  
     Cliquez sur l'onglet **Autorisations** pour indiquer les groupes autorisés à implémenter l'opération.  
  
4.  Cliquez sur **OK** ; l'activité **ReceiveActivity** affiche le nom de l'opération qu'elle implémente.  
  
5.  Ajoutez les activités de workflow à utiliser lors de l'implémentation de cette opération dans l'activité **ReceiveActivity**.  
  
## Voir aussi  
 [Choisir une opération, boîte de dialogue \(héritée\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procédure : appeler une opération de contrat WCF \(héritée\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)