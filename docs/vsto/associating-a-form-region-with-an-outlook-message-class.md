---
title: "Association d’une zone de formulaire à une classe de Message Outlook | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d65b97fa42be6f8c89a2cfd963ce7ad1212b6dc1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="associating-a-form-region-with-an-outlook-message-class"></a>Association d'une zone de formulaire à une classe de message Outlook
  Vous pouvez spécifier les éléments Microsoft Office Outlook qui affichent une zone de formulaire en associant la zone de formulaire de la classe de message de chaque élément. Par exemple, si vous souhaitez ajouter une zone de formulaire au bas d’un élément de messagerie, vous pouvez associer la zone de formulaire avec la gestion intégrée. Notez la classe de message.  
  
 Pour associer une zone de formulaire à une classe de message, spécifiez le nom de classe dans le **nouvelle zone de formulaire Outlook** Assistant ou appliquez un attribut à la classe de fabrique de zones de formulaire.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understanding-outlook-message-classes"></a>Présentation des Classes de Message Outlook  
 Une classe de message Outlook identifie un type d’élément Outlook. Le tableau suivant répertorie ces huit types standards des éléments et leurs noms de classe de message.  
  
|Type d’élément Outlook|Nom de la classe message|  
|-----------------------|------------------------|  
|Objet AppointmentItem|GESTION INTÉGRÉE. Rendez-vous|  
|Objet ContactItem|GESTION INTÉGRÉE. Contact|  
|DistListItem|GESTION INTÉGRÉE. DistList|  
|JournalItem|GESTION INTÉGRÉE. Activité|  
|Objet MailItem|GESTION INTÉGRÉE. Remarque|  
|PostItem|GESTION INTÉGRÉE. Valider ou gestion intégrée. Post.RSS|  
|Objet TaskItem|GESTION INTÉGRÉE. Tâche|  
  
 Vous pouvez également spécifier les noms des classes de message personnalisées. Classes de message personnalisées identifient des formulaires personnalisés que vous définissez dans Outlook.  
  
> [!NOTE]  
>  Pour les zones de formulaire de remplacement et de remplacement, vous pouvez spécifier un nouveau nom de classe de message personnalisé. Vous n’avez pas besoin d’utiliser le nom de classe de message d’un formulaire personnalisé existant. Le nom de la classe de message personnalisée doit être unique. Pour vous assurer que le nom est unique consiste à utiliser une convention d’affectation des noms similaire au suivant : \< *NomClasseMessageStandard*>.\< *Société*>.\< *NomClasseMessage*> (par exemple : gestion intégrée. Note.Contoso.MyMessageClass).  
  
## <a name="associating-a-form-region-with-an-outlook-message-class"></a>Association d'une zone de formulaire à une classe de message Outlook  
 Il existe deux façons d’associer une zone de formulaire avec une classe de message :  
  
-   Utilisez le **nouvelle zone de formulaire Outlook** Assistant.  
  
-   Appliquer des attributs de classe.  
  
### <a name="using-the-new-outlook-form-region-wizard"></a>À l’aide de l’Assistant de zone de formulaire Outlook nouveau  
 Sur la page finale de le **nouvelle zone de formulaire Outlook** Assistant, vous pouvez sélectionner les classes de message standard et tapez les noms des classes de message personnalisées que vous souhaitez associer à la zone de formulaire.  
  
 Les classes de message standard ne sont pas disponibles si la zone de formulaire est conçue pour remplacer l’intégralité du formulaire ou la page par défaut d’un formulaire. Vous pouvez spécifier des noms de classe de message standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés au bas d’un formulaire. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Pour inclure une ou plusieurs classes de message personnalisées, tapez leurs noms dans le **quelles classes de message personnalisées afficheront cette zone de formulaire ?** boîte.  
  
 Les noms que vous tapez doivent respecter les consignes suivantes :  
  
-   Utilisez le nom de classe qualifié complet (par exemple : « gestion intégrée. Note.Contoso »).  
  
-   Utilisez des points-virgules pour séparer plusieurs noms de classe de message.  
  
-   N’incluez pas les classes de message Outlook standard, tels que « gestion intégrée. Remarque » ou « gestion intégrée. Contact ». Inclure uniquement les classes de message personnalisées, telles que « gestion intégrée. Note.Contoso ».  
  
-   Ne spécifiez pas de la classe de base par lui-même (par exemple : « Gestion intégrée »).  
  
-   Ne dépasse pas 256 caractères pour chaque nom de classe de message.  
  
 Le **nouvelle zone de formulaire Outlook** Assistant valide le format de votre saisie lorsque vous cliquez sur **Terminer**.  
  
> [!NOTE]  
>  Le **nouvelle zone de formulaire Outlook** Assistant ne vérifie pas que les noms de classe de message que vous fournissez sont corrects ou valides.  
  
 Lorsque vous terminez l’Assistant, le **nouvelle zone de formulaire Outlook** applique des attributs à la classe de zone de formulaire qui contiennent les noms de classe de message spécifié. Vous pouvez également appliquer ces attributs manuellement.  
  
### <a name="applying-class-attributes"></a>Appliquer des attributs de classe  
 Vous pouvez associer une zone de formulaire à une classe de message Outlook après avoir terminé la **nouvelle zone de formulaire Outlook** Assistant. Pour ce faire, appliquer des attributs à la classe de fabrique de zones de formulaire.  
  
 L’exemple suivant montre deux <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> les attributs qui ont été appliqués à une classe de fabrique de zones de formulaire nommée `myFormRegion`. Le premier attribut associe la zone de formulaire à une classe de message standard pour un formulaire de message électronique. Le deuxième associe la zone de formulaire à une classe de message personnalisée nommée `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Les attributs doivent respecter les consignes suivantes :  
  
-   Pour les classes de message personnalisé, utilisez le nom de classe qualifié complet (par exemple : « gestion intégrée. Note.Contoso »).  
  
-   Ne spécifiez pas de la classe de base par lui-même (par exemple : « Gestion intégrée »).  
  
-   Ne dépasse pas 256 caractères pour chaque nom de classe de message.  
  
-   N’incluez pas les noms des classes de message standard si la zone de formulaire remplace l’intégralité du formulaire ou la page par défaut d’un formulaire. Vous pouvez spécifier des noms de classe de message standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés au bas d’un formulaire. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Visual Studio valide le format des noms de classe de message lorsque vous générez le projet.  
  
> [!NOTE]  
>  Visual Studio ne vérifie pas que les noms de classe de message que vous fournissez sont corrects ou valides.  
  
## <a name="see-also"></a>Voir aussi  
 [L’accès à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Recommandations pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Nom du formulaire et la vue d’ensemble de la classe Message](http://msdn.microsoft.com/library/office/ff867629.aspx)   
 [Fonctionnement des formulaires Outlook et des éléments](http://msdn.microsoft.com/library/office/ff869706.aspx)  
  
  