---
title: "Comment : implémenter une opération de contrat Windows Communication Foundation (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02d6a544b660a110c618bdcb7d3b778fd82ceaaa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : implémenter une opération de contrat Windows Communication Foundation (héritée)
Cette rubrique décrit comment implémenter une opération de contrat [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Après avoir fait glisser un **ReceiveActivity** activité à partir de la boîte à outils vers l’aire de conception de workflow, vous allez soit créer un nouveau [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] de contrat ou importer un contrat existant et implémenter les opérations. Vous sélectionnez ou créez votre contrat et ses opérations par le biais du [opération boîte de dialogue Choisir (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Implémentation d'une opération de contrat WCF  
  
1.  Double-cliquez sur le **ReceiveActivity** activité dans le concepteur ou cliquez sur le bouton de sélection en regard du **ServiceOperationInfo** propriété dans le **propriétés** volet.  
  
2.  Effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur **ajouter un contrat** dans le coin supérieur droit de la boîte de dialogue. Cette opération créera un nouveau contrat [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] ainsi que les opérations correspondantes.  
  
         ou  
  
    -   Cliquez sur **importation** dans le coin supérieur droit de la boîte de dialogue. Le [rechercher et sélectionner une boîte de dialogue du Type .NET (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s’ouvre. Recherchez un assembly ou un projet contenant le contrat souhaité. Sélectionnez le contrat, puis cliquez sur **OK**.  
  
     Une fois un contrat créé ou importé, vous pouvez y ajouter de nouvelles opérations. Pour ajouter une nouvelle opération, sélectionnez le contrat, puis cliquez sur **ajouter une opération** dans le coin supérieur droit de la boîte de dialogue. Lorsque vous avez terminé l'ajout d'opérations, passez à étape 3.  
  
3.  Sélectionnez l’opération que vous souhaitez associer à la **ReceiveActivity** activité. Vous pouvez manipuler la définition de l'opération en modifiant son nom, ses paramètres, ses propriétés et ses paramètres d'autorisation.  
  
     Pour modifier le nom, entrez le nouveau nom dans la **nom de l’opération** zone de texte.  
  
     Cliquez sur le **paramètres** onglet pour accéder aux paramètres de l’opération. Vous pouvez modifier le nom, le type ou la direction d'un paramètre ; il est également possible d'ajouter ou de supprimer des paramètres de l'opération.  
  
     Cliquez sur le **propriétés** tab pour accéder à la fonctionnalité d’exchange opération protection message pris en charge et au niveau de l’opération.  
  
     Cliquez sur le **autorisations** onglet pour spécifier les groupes autorisés à implémenter l’opération.  
  
4.  Cliquez sur **OK** et **ReceiveActivity** activité affiche le nom de l’opération pour l’opération qu’elle implémente.  
  
5.  Placer les activités de flux de travail que vous vous apprêtez à utiliser pour l’implémentation de cette opération dans le **ReceiveActivity** activité.  
  
## <a name="see-also"></a>Voir aussi  
 [Choisissez l’opération, boîte de dialogue (héritée)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)