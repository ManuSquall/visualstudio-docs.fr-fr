---
title: Actions personnalisées dans les zones de formulaire Outlook
description: Découvrez comment les boutons d’affichage d’action, tels que répondre et répondre à tous, permettent aux utilisateurs de répondre à une Microsoft Office élément Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1f95c5bfcd0dda73b3cd3392c5a8b0bb7384bd9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947878"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Actions personnalisées dans les zones de formulaire Outlook
  Les actions affichent des boutons qui permettent aux utilisateurs de répondre à une Microsoft Office élément Outlook. Par exemple, pour répondre à un élément de messagerie, les utilisateurs cliquent sur les boutons **répondre**, **répondre à tous** ou **transférer** l’action. Chacune de ces actions crée un nouvel élément de messagerie et remplit les champs de l’élément à l’aide des informations de l’élément d’origine.

 Vous pouvez créer une action personnalisée qui ouvre n’importe quel type d’élément Outlook. Par exemple, vous pouvez ajouter une action personnalisée qui ouvre un nouveau rendez-vous ou élément de tâche. Définissez les propriétés d’une action personnalisée ou utilisez du code personnalisé pour remplir les champs du nouvel élément. Les actions personnalisées apparaissent dans la liste déroulante **actions personnalisées** d’un élément qui est ouvert dans une fenêtre d’inspecteur Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Ajouter des actions personnalisées à une zone de formulaire
 Pour ajouter une action personnalisée à une zone de formulaire, utilisez la boîte de dialogue **actions personnalisées** . Vous pouvez ouvrir la boîte de dialogue **actions personnalisées** en sélectionnant la zone de formulaire dans **Explorateur de solutions**, en développant le nœud **manifeste** dans la **fenêtre Propriétés**, en sélectionnant la propriété **CustomActions** , puis en cliquant sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")).

 Vous pouvez utiliser la boîte de dialogue **actions personnalisées** pour spécifier un *formulaire cible*. Un formulaire cible est le formulaire qui apparaît lorsque l’utilisateur exécute l’action personnalisée.

 Vous pouvez également utiliser la boîte de dialogue **actions personnalisées** pour spécifier la manière dont vous souhaitez que les informations de l’élément d’origine s’affichent dans le formulaire cible.

 Le tableau suivant décrit les propriétés qui sont disponibles dans la boîte de dialogue **actions personnalisées** .

|Propriété|Description|
|--------------|-----------------|
|**AddressLike**|Spécifie comment le formulaire cible sera adressé.|
|**Corps**|Spécifie comment le corps de l’élément d’origine est ajouté au formulaire cible.|
|**Enabled**|Indique si l’action personnalisée est activée. Si cette propriété a la valeur **false**, l’action personnalisée est désactivée.|
|**Méthode**|Spécifie le type de réponse disponible lors de l’exécution de l’action personnalisée. L’action personnalisée peut envoyer le formulaire, ouvrir le formulaire ou demander à l’utilisateur s’il souhaite envoyer ou ouvrir le formulaire.|
|**Nom**|Spécifie le nom interne que vous pouvez utiliser pour référencer cette action personnalisée dans le code.|
|**ShowOnRibbon**|Indique s’il faut afficher l’action personnalisée sur le ruban de l’élément d’origine.|
|**SubjectPrefix**|Spécifie le texte inséré au début de la ligne d’objet du formulaire cible.|
|**TargetForm**|Spécifie le nom de la classe de message du formulaire cible. Par exemple, tapez **IPM. Tâche** permettant d’ouvrir un formulaire de tâche.|
|**Titre**|Spécifie l’étiquette du bouton d’action personnalisé.|

## <a name="customize-a-custom-action-at-run-time"></a>Personnaliser une action personnalisée au moment de l’exécution
 Vous pouvez également ajouter le comportement à l’action personnalisée à l’aide du code. Par exemple, vous pouvez ajouter du code qui prend les noms des destinataires du courrier électronique et ajoute ces noms en tant que participants dans un nouvel élément de rendez-vous. Pour ce faire, gérez l’événement [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) de l' [objet MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Voir aussi
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
