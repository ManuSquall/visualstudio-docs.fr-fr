---
title: Lier à une activité&#39;boîte de dialogue propriété (hérité) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: bbc9c36bec7c01e7a7e771e7f7145da40b84b177
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211014"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Lier à une activité&#39;boîte de dialogue propriété (hérité)
Cette rubrique décrit comment utiliser le **lier à la propriété d’une activité** boîte de dialogue dans les anciennes [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Vous pouvez lier un type d'instance de propriété de dépendance à la propriété publique ou à un événement d'une autre activité. Pour plus d’informations sur la liaison d’activités, consultez [à l’aide des propriétés de dépendance](http://go.microsoft.com/fwlink?LinkID=65007).  
  
 Vous sélectionnez une propriété à lier à l’aide de la **lier à la propriété d’une activité** boîte de dialogue. Vous ouvrez cette boîte de dialogue en cliquant sur le bouton de sélection **[...]**  à la fin de la zone de texte de la propriété sélectionnée dans le **propriétés** fenêtre, ou en cliquant sur l’icône d’exclamation bleu qui s’affiche en regard du nom de propriété dans l’Explorateur de propriétés.  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **lier à la propriété d’une activité** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Lier à un membre existant**|Sélectionnez un membre avec lequel vous souhaitez établir une liaison dans le volet de l’arborescence. Le volet situé au-dessous de l’arborescence affiche un message qui indique si le membre est un type valide pour la liaison. Cliquez sur **OK** à lier au membre valid sélectionné.|  
|**Lier à un nouveau membre**|Créez un nouveau membre ou une nouvelle propriété à lier. Entrez un **nouveau nom de membre**. Choisissez si vous souhaitez créer une propriété de dépendance ou un champ public en sélectionnant **créer un champ** ou **créer une propriété**. Cliquez sur **OK** pour créer le nouveau membre.|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de l’activité](http://go.microsoft.com/fwlink?LinkID=65013)   
 [À l’aide des propriétés de dépendance](http://go.microsoft.com/fwlink?LinkID=65007)   
 [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)