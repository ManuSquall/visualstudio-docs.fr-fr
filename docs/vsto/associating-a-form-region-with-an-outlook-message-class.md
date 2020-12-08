---
title: Associer une zone de formulaire à une classe de message Outlook
description: Découvrez comment vous pouvez spécifier les Microsoft Office éléments Outlook qui affichent une zone de formulaire en associant la zone de formulaire à la classe de message de chaque élément.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 213b167bf7fe10c83b028fce2d97c67cd837d272
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846998"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associer une zone de formulaire à une classe de message Outlook
  Vous pouvez spécifier les Microsoft Office éléments Outlook qui affichent une zone de formulaire en associant la zone de formulaire à la classe de message de chaque élément. Par exemple, si vous souhaitez ajouter une zone de formulaire au bas d’un élément de messagerie, vous pouvez associer la zone de formulaire à la `IPM.Note` classe de message.

 Pour associer une zone de formulaire à une classe de message, spécifiez le nom de la classe de message dans l’Assistant **nouvelle zone de formulaire Outlook** ou appliquez un attribut à la classe de fabrique de zones de formulaire.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Comprendre les classes de message Outlook
 Une classe de message Outlook identifie un type d’élément Outlook. Le tableau suivant répertorie ces huit types d’éléments standard et leurs noms de classes de messages.

|Type d’élément Outlook|Nom de la classe de message|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` ou `IPM.Post.RSS`|
| TaskItem|`IPM.Task`|

 Vous pouvez également spécifier les noms des classes de message personnalisées. Les classes de message personnalisées identifient les formulaires personnalisés que vous définissez dans Outlook.

> [!NOTE]
> Pour les zones de formulaire de remplacement et de remplacement intégral, vous pouvez spécifier un nouveau nom de classe de message personnalisé. Vous n’avez pas besoin d’utiliser le nom de la classe de message d’un formulaire personnalisé existant. Le nom de la classe de message personnalisée doit être unique. Une façon de s’assurer que le nom est unique est d’utiliser une convention d’affectation de noms similaire à ce qui suit : \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (par exemple : `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associer une zone de formulaire à une classe de message Outlook
 Il existe deux façons d’associer une zone de formulaire à une classe de message :

- Utilisez l’Assistant **nouvelle zone de formulaire Outlook** .

- Appliquez des attributs de classe.

### <a name="use-the-new-outlook-form-region-wizard"></a>Utiliser l’Assistant Nouvelle zone de formulaire Outlook
 Sur la dernière page de l’Assistant **nouvelle zone de formulaire Outlook** , vous pouvez sélectionner les classes de message standard et taper les noms des classes de message personnalisées que vous souhaitez associer à la zone de formulaire.

 Les classes de message standard ne sont pas disponibles si la zone de formulaire est conçue pour remplacer le formulaire entier ou la page par défaut d’un formulaire. Vous pouvez spécifier des noms de classes de messages standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés au bas d’un formulaire. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Pour inclure une ou plusieurs classes de message personnalisées, tapez leurs noms dans la zone **Quelles sont les classes de message personnalisées qui afficheront cette zone de formulaire ?** .

 Les noms que vous tapez doivent respecter les instructions suivantes :

- Utilisez le nom complet de la classe de message (par exemple : «IPM. Remarque. contoso»).

- Utilisez des points-virgules pour séparer plusieurs noms de classes de messages.

- N’incluez pas les classes de message Outlook standard, telles que «IPM. Remarque : « ou » IPM. Contactez». Incluez uniquement les classes de message personnalisées, telles que «IPM. Remarque. contoso».

- Ne spécifiez pas la classe de message de base proprement dite (par exemple : « IPM »).

- Ne dépassez pas 256 caractères pour chaque nom de classe de message.

  L’Assistant **nouvelle zone de formulaire Outlook** valide le format de votre entrée lorsque vous cliquez sur **Terminer**.

> [!NOTE]
> L’Assistant **nouvelle zone de formulaire Outlook** ne vérifie pas si les noms de classe de message que vous fournissez sont corrects ou valides.

 Lorsque vous terminez l’Assistant, l’Assistant **nouvelle zone de formulaire Outlook** applique des attributs à la classe de zone de formulaire qui contient les noms de classe de message spécifiés. Vous pouvez également appliquer ces attributs manuellement.

### <a name="apply-class-attributes"></a>Appliquer les attributs de classe
 Vous pouvez associer une zone de formulaire à une classe de message Outlook une fois que vous avez terminé l’Assistant **nouvelle zone de formulaire Outlook** . Pour ce faire, appliquez des attributs à la classe de fabrique de zones de formulaire.

 L’exemple suivant montre deux <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> attributs qui ont été appliqués à une classe de fabrique de zones de formulaire nommée `myFormRegion` . Le premier attribut associe la zone de formulaire à une classe de message standard pour un formulaire de message électronique. Le deuxième attribut associe la zone de formulaire à une classe de message personnalisée nommée `IPM.Task.Contoso` .

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Les attributs doivent respecter les instructions suivantes :

- Pour les classes de message personnalisées, utilisez le nom complet de la classe de message (par exemple : «IPM. Remarque. contoso»).

- Ne spécifiez pas la classe de message de base proprement dite (par exemple : « IPM »).

- Ne dépassez pas 256 caractères pour chaque nom de classe de message.

- N’incluez pas les noms des classes de message standard si la zone de formulaire remplace la totalité du formulaire ou la page par défaut d’un formulaire. Vous pouvez spécifier des noms de classes de messages standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés au bas d’un formulaire. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Visual Studio valide le format des noms de classe de message lorsque vous générez le projet.

> [!NOTE]
> Visual Studio ne vérifie pas que les noms de classe de message que vous fournissez sont corrects ou valides.

## <a name="see-also"></a>Voir aussi
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instructions pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Vue d’ensemble du nom de formulaire et de la classe de message](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Comment les formulaires et les éléments Outlook fonctionnent ensemble](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
