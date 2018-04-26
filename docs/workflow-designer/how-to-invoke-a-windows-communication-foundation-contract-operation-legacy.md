---
title: 'Le Concepteur de flux de travail - Comment : appeler une opération de contrat Windows Communication Foundation (hérité)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b39d2132b29ec1f8fbfd8339bdb8f81e6f752a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : appeler une opération de contrat Windows Communication Foundation (héritée)

Cette rubrique décrit comment appeler une opération de contrat de Windows Communication Foundation (WCF) en utilisant le Concepteur de flux de travail Windows hérité qui cible le .NET Framework version 3.5 ou le WinFX.

Une fois que vous faites glisser un **SendActivity** activité à partir de la boîte à outils vers l’aire de conception du flux de travail, importer un contrat existant. Déterminer quelle opération est appelée à partir de ce **SendActivity** activité. Sélectionnez le contrat et ses opérations via le [opération boîte de dialogue Choisir (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md).

En outre, si vous utilisez un fichier de configuration avec votre service, vous devez spécifier un <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifie la configuration de point de terminaison qui sera utilisée par l'activité d'envoi pour se connecter au service de workflow.

## <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Appel d'une opération de contrat WCF à partir d'une activité SendActivity

1.  Double-cliquez sur le **SendActivity** activité dans le concepteur ou cliquez sur le bouton de sélection en regard du **ServiceOperationInfo** propriété dans le **propriétés** volet.

2.  Lorsque le **choisir une opération** boîte de dialogue s’ouvre, cliquez sur **importation** dans le coin supérieur droit de la boîte de dialogue.

     Le [rechercher et sélectionner une boîte de dialogue du Type .NET (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s’ouvre.

3.  Recherchez un assembly ou un projet contenant le contrat souhaité.

4.  Sélectionnez le contrat, puis cliquez sur **OK**.

5.  Sous **opérations disponibles**, sélectionnez l’opération que vous souhaitez appeler et cliquez sur **OK**.

## <a name="to-specify-a-channel-token"></a>Indication d'un jeton de canal

1.  Sélectionnez l'activité <xref:System.Workflow.Activities.SendActivity> dans le concepteur.

2.  Dans le **propriétés** volet, spécifiez un nom pour le <xref:System.Workflow.Activities.ChannelToken>. Ce nom identifie uniquement le jeton de canal.

3.  Développez le nœud du jeton de canal et indiquez un nom pour le point de terminaison client à utiliser dans le champ <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuration de point de terminaison du même nom dans le fichier de configuration est utilisée pour configurer le canal.

4.  Créez la configuration de point de terminaison dans le fichier de configuration, s'il n'existe pas déjà. Pour plus d’informations sur la configuration de votre client, consultez [vue d’ensemble du Client WCF](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Voir aussi

- [Choisir une opération, boîte de dialogue (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)