---
title: Choisir une opération, boîte de dialogue (héritée) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659158"
---
# <a name="choose-operation-dialog-box-legacy"></a>Choisir une opération, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **choisir une opération** dans le hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 La boîte de dialogue **choisir une opération** permet de sélectionner une opération à associer à une <xref:System.Workflow.Activities.ReceiveActivity> activité ou à une <xref:System.Workflow.Activities.SendActivity> activité. Pour plus d’informations sur l’utilisation de cette boîte de dialogue avec ces activités, consultez [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) et [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **choisir une opération** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Ajouter un contrat**|Crée un contrat. Vous pouvez y définir de nouvelles opérations (Cette opération est utilisée uniquement avec <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Ajouter une opération**|Ajoute de nouvelles opérations à un nouveau contrat que vous avez créé dans la boîte de dialogue **choisir une opération** . **Remarque :**  Vous pouvez ajouter de nouvelles opérations uniquement aux contrats que vous avez créés par le biais de la boîte de dialogue **choisir une opération** . <br /><br /> (Cette opération est utilisée uniquement avec <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Importer...**|Importe un contrat défini précédemment et permet de sélectionner une opération faisant partie de ce contrat.|
|**Nom d’opération**|Nom de l'opération actuellement sélectionnée. Cette zone de texte peut être modifiée uniquement si vous avez créé une opération à l’aide de la boîte de dialogue **choisir une opération** .|
|**Paramètres**|Onglet contenant les définitions des paramètres pour l'opération actuellement sélectionnée. **Remarque :**  Les définitions de paramètres ne peuvent être modifiées que si vous avez créé une opération à l’aide de la boîte de dialogue **choisir une opération** .|
|**Propriétés**|Onglet contenant les paramètres du <xref:System.Net.Security.ProtectionLevel> correspondant aux messages envoyés entre le client et service. **Remarque :**  Cet onglet est activé uniquement si vous avez créé une opération à l’aide de la boîte de dialogue **choisir une opération** .|
|**autorisations**|Onglet contenant les propriétés <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> et <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> des utilisateurs autorisés à appeler cette opération. Par exemple, si seuls les utilisateurs du groupe administrateurs étaient autorisés à appeler cette opération, vous écririez « administrateurs » dans la zone de texte **rôle** .<br /><br /> Cet onglet est activé pour les deux opérations créées via la boîte de dialogue **ChooseOperation** et les opérations qui ont été importées via le bouton **Importer** .|

> [!NOTE]
> La boîte de dialogue **choisir une opération** affiche uniquement les contrats ou les opérations utilisés par <xref:System.Workflow.Activities.SendActivity> d’autres activités dans le flux de travail. De même, la boîte de dialogue **choisir une opération** pour <xref:System.Workflow.Activities.ReceiveActivity> les activités affiche uniquement les contrats ou les opérations utilisés par d’autres activités **ReceiveActivity** dans le flux de travail.

## <a name="see-also"></a>Voir aussi
 [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Concepteur hérité pour Windows Workflow Foundation aide de l’interface utilisateur](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)