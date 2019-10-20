---
title: 'Comment : appeler une opération de contrat de Windows Communication Foundation (héritée) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603702"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : appeler une opération de contrat Windows Communication Foundation (héritée)
Cette rubrique décrit comment appeler une opération de contrat [!INCLUDE[indigo1](../includes/indigo1-md.md)] à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Après avoir fait glisser une activité **SendActivity** de la boîte à outils vers l’aire de conception de workflow, vous devez importer un contrat existant et déterminer l’opération qui sera appelée à partir de cette activité **SendActivity** . Vous sélectionnez votre contrat et ses opérations via la [boîte de dialogue choisir une opération (héritée)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Par ailleurs, si vous utilisez un fichier de configuration avec votre service, vous devrez indiquer un jeton <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifie la configuration de point de terminaison qui sera utilisée par l'activité d'envoi pour se connecter au service de workflow.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Appel d'une opération de contrat WCF à partir d'une activité SendActivity

1. Double-cliquez sur l’activité **SendActivity** dans le concepteur ou cliquez sur les points de suspension en regard de la propriété **ServiceOperationInfo** dans le volet **Propriétés** .

2. Quand la boîte de dialogue **choisir une opération** s’ouvre, cliquez sur **Importer** dans l’angle supérieur droit de la boîte de dialogue.

     La boîte de [dialogue Parcourir et sélectionner un type .net (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s’ouvre.

3. Recherchez un assembly ou un projet contenant le contrat souhaité.

4. Sélectionnez le contrat, puis cliquez sur **OK**.

5. Sous **opérations disponibles**, sélectionnez l’opération que vous souhaitez appeler, puis cliquez sur **OK**.

### <a name="to-specify-a-channel-token"></a>Indication d'un jeton de canal

1. Sélectionnez l'activité <xref:System.Workflow.Activities.SendActivity> dans le concepteur.

2. Dans le volet **Propriétés** , spécifiez un nom pour le <xref:System.Workflow.Activities.ChannelToken>. Ce nom identifie uniquement le jeton de canal.

3. Développez le nœud du jeton de canal et indiquez un nom pour le point de terminaison client à utiliser dans le champ <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuration de point de terminaison correspondant au même nom dans le fichier de configuration sera utilisée pour configurer le canal.

4. Créez la configuration de point de terminaison dans le fichier de configuration, s'il n'existe pas déjà. Pour plus d’informations sur la configuration de votre client, consultez [vue d’ensemble du client WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Voir aussi
 [Choisir une opération, boîte de dialogue (héritée)](../workflow-designer/choose-operation-dialog-box-legacy.md) [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)