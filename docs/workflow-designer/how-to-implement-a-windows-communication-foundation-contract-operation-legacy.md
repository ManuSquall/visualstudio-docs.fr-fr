---
title: 'Le Concepteur de flux de travail - Comment : implémenter une opération de contrat Windows Communication Foundation (hérité)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b069d8ca8c1adb72e2869eb59644e8abeff14ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979020"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : implémenter une opération de contrat Windows Communication Foundation (héritée)

Cette rubrique décrit comment implémenter une opération de contrat de Windows Communication Foundation (WCF) en utilisant le Concepteur de flux de travail Windows hérité qui cible le .NET Framework version 3.5 ou le WinFX.

Après avoir fait glisser un **ReceiveActivity** activité à partir de la boîte à outils vers l’aire de conception de workflow, vous allez soit créer un nouveau [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] de contrat ou importer un contrat existant et implémenter les opérations. Vous sélectionnez ou créez votre contrat et ses opérations par le biais du [opération boîte de dialogue Choisir (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md).

## <a name="to-implement-a-wcf-contract-operation"></a>Implémentation d'une opération de contrat WCF

1.  Double-cliquez sur le **ReceiveActivity** activité dans le concepteur ou cliquez sur le bouton de sélection en regard du **ServiceOperationInfo** propriété dans le **propriétés** volet.

2.  Effectuez l’une des opérations suivantes :

    -   Cliquez sur **ajouter un contrat** dans le coin supérieur droit de la boîte de dialogue. Cette opération créera un nouveau contrat [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] ainsi que les opérations correspondantes.

         - ou -

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

- [Choisir une opération, boîte de dialogue (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)