---
title: "Choisissez l’opération, boîte de dialogue (héritée) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 2db745d34c86e4b0aa5639872106096421044bce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="choose-operation-dialog-box-legacy"></a>Choisir une opération, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser le **choisir une opération** boîte de dialogue de l’héritage [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Le **choisir une opération** boîte de dialogue permet de sélectionner une opération à associer à un <xref:System.Workflow.Activities.ReceiveActivity> activité ou un <xref:System.Workflow.Activities.SendActivity> activité. Pour plus d’informations sur l’utilisation de cette boîte de dialogue avec ces activités, consultez [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) et [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **choisir une opération** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Ajouter un contrat**|Crée un contrat. Vous pouvez y définir de nouvelles opérations (Cette opération est utilisée uniquement avec <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**L’opération d’ajout**|Ajoute de nouvelles opérations à un contrat que vous avez créé dans le **choisir une opération** boîte de dialogue. **Remarque :** vous pouvez ajouter de nouvelles opérations uniquement aux contrats créés par le biais du **choisir une opération** boîte de dialogue. <br /><br /> (Cette opération est utilisée uniquement avec <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**Importation en cours...**|Importe un contrat défini précédemment et permet de sélectionner une opération faisant partie de ce contrat.|  
|**Nom de l’opération**|Nom de l'opération actuellement sélectionnée. Cette zone de texte peut être modifiée uniquement si vous avez créé une opération via le **choisir une opération** boîte de dialogue.|  
|**Paramètres**|Onglet contenant les définitions des paramètres pour l'opération actuellement sélectionnée. **Remarque :** définitions de paramètres peuvent être modifiées uniquement si vous avez créé une opération via le **choisir une opération** boîte de dialogue.|  
|**Propriétés**|Onglet contenant les paramètres du <xref:System.Net.Security.ProtectionLevel> correspondant aux messages envoyés entre le client et service. **Remarque :** cet onglet est activé uniquement si vous avez créé une opération via le **choisir une opération** boîte de dialogue.|  
|**Autorisations**|Onglet contenant les propriétés <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> et <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> des utilisateurs autorisés à appeler cette opération. Par exemple, si seuls les utilisateurs du groupe Administrateurs ont été autorisés à appeler cette opération, puis vous écririez « Administrateurs » le **rôle** zone de texte.<br /><br /> Cet onglet est activé pour les deux opérations créées via le **ChooseOperation** boîte de dialogue et les opérations qui ont été importées par le biais du **importation** bouton.|  
  
> [!NOTE]
>  Le **choisir une opération** boîte de dialogue affiche uniquement les contrats ou les opérations qui sont utilisées par d’autres <xref:System.Workflow.Activities.SendActivity> activités dans le flux de travail. De même, la **choisir une opération** boîte de dialogue <xref:System.Workflow.Activities.ReceiveActivity> activités affiche uniquement les contrats ou les opérations qui sont utilisées par d’autres **ReceiveActivity** activités dans le flux de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Comment : appeler une opération de contrat WCF (héritée)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)