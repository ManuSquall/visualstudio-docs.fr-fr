---
title: "Choisir une op&#233;ration, bo&#238;te de dialogue (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Choisir une op&#233;ration, bo&#238;te de dialogue (h&#233;rit&#233;e)
Cette rubrique décrit comment utiliser la boîte de dialogue **Choisir une opération** dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 La boîte de dialogue **Choisir une opération** permet de sélectionner une opération à associer à une activité <xref:System.Workflow.Activities.ReceiveActivity> ou <xref:System.Workflow.Activities.SendActivity>.Pour plus d'informations sur l'utilisation de la boîte de dialogue avec ces activités, consultez [Procédure : implémenter une opération de contrat WCF \(héritée\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) et [Procédure : appeler une opération de contrat WCF \(héritée\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 Le tableau suivant décrit les éléments d'interface utilisateur \(UI\) de la boîte de dialogue **Choisir une opération**.  
  
|Élément d'interface|Description|  
|-------------------------|-----------------|  
|**Ajouter un contrat**|Crée un contrat.Vous pouvez y définir de nouvelles opérations\(cette opération est utilisée uniquement avec <xref:System.Workflow.Activities.ReceiveActivity>\).|  
|**Ajouter une  opération**|Ajoute de nouvelles opérations à un contrat créé à l'aide de la boîte de dialogue **Choisir une opération**. **Note:**  Vous pouvez ajouter de nouvelles opérations uniquement aux contrats créés à l'aide de la boîte de dialogue **Choisir une opération**. <br /><br /> \(Cette opération est utilisée uniquement avec <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Importer...**|Importe un contrat défini précédemment et permet de sélectionner une opération faisant partie de ce contrat.|  
|**Nom de l'opération**|Nom de l'opération actuellement sélectionnée.Cette zone de texte peut être modifiée uniquement si vous avez créé une opération à l'aide de la boîte de dialogue **Choisir une opération**.|  
|**Paramètres**|Onglet contenant les définitions des paramètres pour l'opération actuellement sélectionnée. **Note:**  Les définitions des paramètres peuvent être modifiées uniquement si vous avez créé une opération à l'aide de la boîte de dialogue **Choisir une opération**.|  
|**Propriétés**|Onglet contenant les paramètres du <xref:System.Net.Security.ProtectionLevel> correspondant aux messages envoyés entre le client et service. **Note:**  Cet onglet est activé uniquement si vous avez créé une opération à l'aide de la boîte de dialogue **Choisir une opération**.|  
|**Autorisations**|Onglet contenant les propriétés <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> et <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> des utilisateurs autorisés à appeler cette opération.Par exemple, si seuls les utilisateurs du groupe Administrateurs sont autorisés à appeler cette opération, indiquez "Administrateurs" dans la zone de texte **Rôle**.<br /><br /> Cet onglet est activé pour les deux opérations créées à l'aide de la boîte de dialogue **Choisir une opération**, ainsi que pour celles importées à l'aide du bouton **Importer**.|  
  
> [!NOTE]
>  La boîte de dialogue **Choisir une opération** affiche uniquement les contrats ou les opérations utilisés par d'autres activités <xref:System.Workflow.Activities.SendActivity> du workflow.Par ailleurs, la boîte de dialogue **Choisir une opération** correspondant aux activités <xref:System.Workflow.Activities.ReceiveActivity> affiche uniquement les contrats ou les opérations utilisés par d'autres activités **ReceiveActivity** du workflow.  
  
## Voir aussi  
 [Procédure : implémenter une opération de contrat WCF \(héritée\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Procédure : appeler une opération de contrat WCF \(héritée\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Aide de l'interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)