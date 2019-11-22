---
title: Boîte de dialogue lier&#39;à une propriété d’activité (héritée) | Microsoft Docs
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
ms.openlocfilehash: 451544a84237bc6fa4e069df9dd1e17feccf86f7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301011"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Boîte de dialogue lier&#39;à une propriété d’activité (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **Lier à la propriété d'une activité** dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Vous pouvez lier un type d'instance de propriété de dépendance à la propriété publique ou à un événement d'une autre activité. Pour plus d’informations sur la liaison d’activité, consultez [utilisation des propriétés de dépendance](https://go.microsoft.com/fwlink?LinkID=65007).

 Pour sélectionner une propriété avec laquelle vous souhaitez créer une liaison, utilisez la boîte de dialogue **Lier à la propriété d'une activité**. Pour ouvrir cette boîte de dialogue, cliquez sur les boutons de sélection **[.]** à la fin de la zone de texte de la propriété sélectionnée dans la fenêtre **Propriétés**, ou encore cliquez sur l'icône contenant un point d'exclamation bleu, qui figure à côté du nom de la propriété dans l'explorateur de propriétés.

 Le tableau suivant décrit les éléments d'interface utilisateur de la boîte de dialogue **Lier à la propriété d'une activité**.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Lier à un membre existant**|Sélectionnez un membre avec lequel vous souhaitez établir une liaison dans le volet de l’arborescence. Le volet situé au-dessous de l’arborescence affiche un message qui indique si le membre est un type valide pour la liaison. Cliquez sur **OK** pour créer une liaison avec le membre valide sélectionné.|
|**Lier à un nouveau membre**|Créez un nouveau membre ou une nouvelle propriété à lier. Entrez un nom dans **Nom du nouveau membre**. Choisissez si vous souhaitez créer une propriété de dépendance ou un champ public ; pour cela, sélectionnez **Créer un champ** ou **Créer une propriété**. Cliquez sur **OK** pour créer le nouveau membre.|

## <a name="see-also"></a>Voir aussi
 [Utilisation des propriétés](https://go.microsoft.com/fwlink?LinkID=65013) de [l’activité à l'](https://go.microsoft.com/fwlink?LinkID=65007) aide des propriétés [de dépendance concepteur hérité pour Windows Workflow Foundation l’aide de l’interface utilisateur](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)