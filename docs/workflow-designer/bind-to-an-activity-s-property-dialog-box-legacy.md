---
title: Lier à une activité&#39;boîte de dialogue propriété (hérité) | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a799b57169116343f5d83e54ce5bd87dedfd801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Lier à une activité&#39;boîte de dialogue propriété (hérité)
Cette rubrique décrit comment utiliser le **lier à la propriété d’une activité** boîte de dialogue dans le Concepteur de flux de travail Windows hérité. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Vous pouvez lier un type d'instance de propriété de dépendance à la propriété publique ou à un événement d'une autre activité. Pour plus d’informations sur la liaison d’activité, consultez [à l’aide des propriétés de dépendance](http://go.microsoft.com/fwlink?LinkID=65007).

 Vous sélectionnez une propriété à lier à l’aide de la **lier à la propriété d’une activité** boîte de dialogue. Vous ouvrez cette boîte de dialogue en cliquant sur les points de suspension **[...]**  à la fin de la zone de texte de la propriété sélectionnée dans le **propriétés** fenêtre, ou en cliquant sur l’icône de point d’exclamation bleu s’affiche en regard du nom de propriété dans l’Explorateur de propriétés.

 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **lier à la propriété d’une activité** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Lier à un membre existant**|Sélectionnez un membre avec lequel vous souhaitez établir une liaison dans le volet de l’arborescence. Le volet situé au-dessous de l’arborescence affiche un message qui indique si le membre est un type valide pour la liaison. Cliquez sur **OK** à lier à un membre valid sélectionné.|
|**Lier à un nouveau membre**|Créez un nouveau membre ou une nouvelle propriété à lier. Entrez un **nom du nouveau membre**. Indiquez si vous voulez créer une propriété de dépendance ou un champ public en sélectionnant **créer un champ** ou **créer une propriété**. Cliquez sur **OK** pour créer le nouveau membre.|

## <a name="see-also"></a>Voir aussi

- [À l’aide des propriétés de l’activité](http://go.microsoft.com/fwlink?LinkID=65013)
- [À l’aide des propriétés de dépendance](http://go.microsoft.com/fwlink?LinkID=65007)
- [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)