---
title: Boîte de dialogue lier à une activité&#39;s (héritée) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f88d7ebe714fcdc9bf404e1cf58c4c86cf37047d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851470"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Boîte de dialogue Propriétés de lier à une activité&#39;s (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **lier à la propriété d’une activité** dans le hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Vous pouvez lier un type d'instance de propriété de dépendance à la propriété publique ou à un événement d'une autre activité. Pour plus d’informations sur la liaison d’activité, consultez [utilisation des propriétés de dépendance](https://msdn2.microsoft.com/library/bb675255.aspx).

 Vous sélectionnez une propriété à lier à l’aide de la boîte de dialogue **lier à la propriété d’une activité** . Pour ouvrir cette boîte de dialogue, cliquez sur les points de suspension **[...]** à la fin de la zone de texte de la propriété sélectionnée dans la fenêtre **Propriétés** , ou cliquez sur l’icône de point d’exclamation bleue qui s’affiche en regard du nom de la propriété dans l’Explorateur de propriétés.

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue de **Propriétés lier à la propriété d’une activité** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Lier à un membre existant**|Sélectionnez un membre avec lequel vous souhaitez établir une liaison dans le volet de l’arborescence. Le volet situé au-dessous de l’arborescence affiche un message qui indique si le membre est un type valide pour la liaison. Cliquez sur **OK** pour établir une liaison avec le membre valide sélectionné.|
|**Lier à un nouveau membre**|Créez un nouveau membre ou une nouvelle propriété à lier. Entrez un **nouveau nom de membre**. Choisissez si vous souhaitez créer une propriété de dépendance ou un champ public en sélectionnant **créer un champ** ou **créer une propriété**. Cliquez sur **OK** pour créer le nouveau membre.|

## <a name="see-also"></a>Voir aussi
 [Utilisation des propriétés](https://msdn2.microsoft.com/library/bb628510.aspx) de [l’activité à l'](https://msdn2.microsoft.com/library/bb675255.aspx) aide des propriétés [de dépendance concepteur hérité pour Windows Workflow Foundation l’aide de l’interface utilisateur](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
