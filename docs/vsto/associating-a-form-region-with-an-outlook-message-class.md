---
title: Associer une zone de formulaire à une classe de message Outlook
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c264048887d3a1ba77d498784dc3e6cc4384159
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440360"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associer une zone de formulaire à une classe de message Outlook
  Vous pouvez spécifier les éléments Microsoft Office Outlook qui affichent une zone de formulaire en associant la zone de formulaire à la classe de message de chaque élément. Par exemple, si vous souhaitez ajouter une zone de formulaire au bas d’un élément de messagerie, vous pouvez associer la zone de formulaire avec le `IPM.Note` classe de message.

 Pour associer une zone de formulaire à une classe de message, spécifiez le nom de classe de message dans le **nouvelle zone de formulaire Outlook** Assistant ou appliquez un attribut à la classe de fabrique de zones de formulaire.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Comprendre les classes de message Outlook
 Une classe de message Outlook identifie un type d’élément Outlook. Le tableau suivant répertorie ces huit types standards des éléments et leurs noms de classe de message.

|Type d’élément Outlook|Nom de la classe message|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` ou `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Vous pouvez également spécifier les noms des classes de message personnalisées. Classes de message personnalisées identifient des formulaires personnalisés que vous définissez dans Outlook.

> [!NOTE]
> Pour le remplacement et de zones de formulaire de remplacement global, vous pouvez spécifier un nouveau nom de classe de message personnalisé. Vous n’avez pas besoin d’utiliser le nom de classe de message d’un formulaire personnalisé existant. Le nom de la classe de message personnalisée doit être unique. Pour vous assurer que le nom est unique consiste à utiliser une convention d’affectation de noms similaire à ce qui suit : \<*NomClasseMessageStandard*>.\< *Entreprise*>.\< *NomClasseMessage*> (par exemple : `IPM.Note.Contoso.MyMessageClass`).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associer une zone de formulaire à une classe de message Outlook
 Il existe deux façons pour associer une zone de formulaire à une classe de message :

- Utilisez le **nouvelle zone de formulaire Outlook** Assistant.

- Appliquer des attributs de classe.

### <a name="use-the-new-outlook-form-region-wizard"></a>Utilisez l’Assistant Nouvelle zone de formulaire Outlook
 Sur la page finale de le **nouvelle zone de formulaire Outlook** Assistant, vous pouvez sélectionner les classes de message standard et tapez les noms des classes de message personnalisées que vous souhaitez associer à la zone de formulaire.

 Les classes de message standard ne sont pas disponibles si la zone de formulaire est conçue pour remplacer la totalité du formulaire ou la page par défaut d’un formulaire. Vous pouvez spécifier des noms de classe de message standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés au bas d’un formulaire. Pour plus d'informations, voir [Procédure : Ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Pour inclure une ou plusieurs classes de message personnalisées, tapez leurs noms dans le **quelles classes de message personnalisées afficheront cette zone de formulaire ?** boîte.

 Les noms que vous tapez doivent respecter les consignes suivantes :

- Utiliser le nom de classe qualifié complet (par exemple : "IPM.Note.Contoso").

- Utilisez des points-virgules pour séparer plusieurs noms de classe de message.

- N’incluez pas les classes de message Outlook standard, tels que « gestion intégrée. Remarque » ou « gestion intégrée. Contact ». Inclure uniquement les classes de message personnalisées, telles que « gestion intégrée. Note.Contoso ».

- Ne spécifiez pas de la classe de message de base en lui-même (par exemple : "IPM").

- Ne dépasse pas 256 caractères pour chaque nom de classe de message.

  Le **nouvelle zone de formulaire Outlook** Assistant valide le format de votre saisie, lorsque vous cliquez sur **Terminer**.

> [!NOTE]
> Le **nouvelle zone de formulaire Outlook** Assistant ne vérifie pas que les noms de classe de message que vous fournissez sont corrects ou valides.

 Lorsque vous terminez l’Assistant, le **nouvelle zone de formulaire Outlook** applique des attributs à la classe de zones de formulaire qui contiennent les noms de classe de message spécifié. Vous pouvez également appliquer ces attributs manuellement.

### <a name="apply-class-attributes"></a>Appliquer des attributs de classe
 Vous pouvez associer une zone de formulaire à une classe de message Outlook après avoir terminé la **nouvelle zone de formulaire Outlook** Assistant. Pour ce faire, appliquer des attributs à la classe de fabrique de zones de formulaire.

 L’exemple suivant montre deux <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> attributs qui ont été appliqués à une classe de fabrique de zones de formulaire nommée `myFormRegion`. Le premier attribut associe la zone de formulaire à une classe de message standard pour un formulaire de message électronique. Le deuxième attribut associe la zone de formulaire à une classe de message personnalisée nommée `IPM.Task.Contoso`.

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Les attributs doivent respecter les consignes suivantes :

- Pour les classes de message personnalisé, utilisez le nom de classe qualifié complet (par exemple : "IPM.Note.Contoso").

- Ne spécifiez pas de la classe de message de base en lui-même (par exemple : "IPM").

- Ne dépasse pas 256 caractères pour chaque nom de classe de message.

- N’incluez pas les noms des classes de message standard si la zone de formulaire remplace l’intégralité du formulaire ou la page par défaut d’un formulaire. Vous pouvez spécifier des noms de classe de message standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés au bas d’un formulaire. Pour plus d'informations, voir [Procédure : Ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Visual Studio valide le format des noms de classe de message lorsque vous générez le projet.

> [!NOTE]
> Visual Studio ne vérifie pas que les noms de classe de message que vous fournissez sont corrects ou valides.

## <a name="see-also"></a>Voir aussi
- [Accéder à une zone de formulaire lors de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Procédure pas à pas : Concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instructions pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Nom du formulaire et classes de messages vue d’ensemble](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Fonctionnement des formulaires Outlook et des éléments](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
