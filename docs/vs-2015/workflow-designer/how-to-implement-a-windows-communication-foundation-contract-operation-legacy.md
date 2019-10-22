---
title: 'Comment : implémenter une opération de contrat de Windows Communication Foundation (héritée) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603866"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : implémenter une opération de contrat Windows Communication Foundation (héritée)
Cette rubrique décrit comment implémenter une opération de contrat [!INCLUDE[indigo1](../includes/indigo1-md.md)] à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Après avoir fait glisser une activité **ReceiveActivity** de la boîte à outils vers l’aire de conception de workflow, vous créez un contrat de [!INCLUDE[indigo2](../includes/indigo2-md.md)] ou importez un contrat existant et implémentez les opérations. Vous sélectionnez et/ou créez votre contrat et ses opérations via la [boîte de dialogue choisir une opération (héritée)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Implémentation d'une opération de contrat WCF

1. Double-cliquez sur l’activité **ReceiveActivity** dans le concepteur ou cliquez sur les points de suspension en regard de la propriété **ServiceOperationInfo** dans le volet **Propriétés** .

2. Effectuez l’une des opérations suivantes :

   - Cliquez sur **Ajouter un contrat** dans l’angle supérieur droit de la boîte de dialogue. Cette opération créera un nouveau contrat [!INCLUDE[indigo2](../includes/indigo2-md.md)] ainsi que les opérations correspondantes.

      ou

   - Cliquez sur **Importer** dans l’angle supérieur droit de la boîte de dialogue. La boîte de [dialogue Parcourir et sélectionner un type .net (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s’ouvre. Recherchez un assembly ou un projet contenant le contrat souhaité. Sélectionnez le contrat, puis cliquez sur **OK**.

     Une fois un contrat créé ou importé, vous pouvez y ajouter de nouvelles opérations. Pour ajouter une nouvelle opération, sélectionnez le contrat, puis cliquez sur **Ajouter une opération** dans l’angle supérieur droit de la boîte de dialogue. Lorsque vous avez terminé l'ajout d'opérations, passez à étape 3.

3. Sélectionnez l’opération que vous souhaitez associer à l’activité **ReceiveActivity** . Vous pouvez manipuler la définition de l'opération en modifiant son nom, ses paramètres, ses propriétés et ses paramètres d'autorisation.

    Pour modifier le nom, entrez le nouveau nom dans la zone de texte nom de l' **opération** .

    Cliquez sur l’onglet **paramètres** pour accéder aux paramètres de l’opération. Vous pouvez modifier le nom, le type ou la direction d'un paramètre ; il est également possible d'ajouter ou de supprimer des paramètres de l'opération.

    Cliquez sur l’onglet **Propriétés** pour accéder au niveau de protection de l’opération et à la fonctionnalité d’échange de messages prise en charge de l’opération.

    Cliquez sur l’onglet **autorisations** pour spécifier le ou les groupes autorisés à implémenter l’opération.

4. Cliquez sur **OK** pour que l’activité **ReceiveActivity** affiche le nom de l’opération qu’elle implémente.

5. Placez les activités de flux de travail que vous allez utiliser pour l’implémentation de cette opération dans l’activité **ReceiveActivity** .

## <a name="see-also"></a>Voir aussi
 [Choisir une opération, boîte de dialogue (héritée)](../workflow-designer/choose-operation-dialog-box-legacy.md) [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)