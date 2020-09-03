---
title: Instructions pour la création de zones de formulaire Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a962b1ae2bff7b9a954204485a6ee73a3b63eb7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255951"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Instructions pour créer des zones de formulaire Outlook
  Les informations suivantes peuvent vous aider à optimiser vos zones de formulaire et à éviter d’éventuels problèmes :

- [Utilisez des noms de zones de formulaire](#UsingFormRegions).

- [Désactive l’héritage de zone de formulaire](#DisablingInheritance).

- [Comprendre les types et les noms de classes de messages](#ClassNames).

- [Concevez les zones de formulaire adjacentes pour le volet de lecture](#ReadingPane).

- [Utilisez des tailles d’icône optimales](#UsingOptimal).

  Pour plus d’informations sur les zones de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Utiliser des noms de zones de formulaire
 Plusieurs noms décrivent la zone de formulaire. Il est important de comprendre la différence entre ces noms et leur impact sur la zone de formulaire. Le tableau suivant décrit chaque nom.

|Nom de zone de formulaire|Description|
|----------------------|-----------------|
|Nom d’élément de zone de formulaire|Nom que vous spécifiez pour l’élément **Zone de formulaire Outlook** dans la boîte de dialogue **Ajouter un nouvel élément** . Il s’agit du nom du fichier de code de zone de formulaire affiché dans l’ **Explorateur de solutions**.|
|Propriété<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>|Vous spécifiez ce nom dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d’affichage** de l’Assistant **Nouvelle zone de formulaire Outlook** . Ce nom apparaît comme propriété **FormRegionName** dans la fenêtre **Propriétés** .<br /><br /> Utilisez la propriété <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> pour spécifier l’étiquette qui identifie la zone de formulaire dans l’interface utilisateur d’Outlook. Pour les zones de formulaire distinctes, ce nom s’affiche sous forme de bouton dans le ruban de l’élément Outlook.<br /><br /> Pour les zones de formulaire adjacentes, ce nom s’affiche sous forme de texte d’en-tête au-dessus de la zone de formulaire.|
|Attribut `Microsoft.Office.Tools.Outlook.FormRegionName`|Quand vous ajoutez un élément **Zone de formulaire Outlook** au projet, Visual Studio affecte à cette propriété le nom qualifié complet de la zone de formulaire. Le nom qualifié complet par défaut est le nom du complément VSTO associé au nom de la zone de formulaire par un point, par exemple `OutlookAddIn1.FormRegion1`.<br /><br /> Ce nom qualifié complet apparaît également en tant qu’attribut en haut de la classe de fabrique de zones de formulaire.<br /><br /> Utilisez l' `Microsoft.Office.Tools.Outlook.FormRegionName` attribut pour identifier de façon unique la zone de formulaire dans tous les compléments VSTO Outlook. Vous ne pouvez pas modifier la valeur de l' `Microsoft.Office.Tools.Outlook.FormRegionName` attribut en renommant l’élément de zone de formulaire ou en modifiant la <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriété. Pour modifier ce nom, vous devez modifier l’attribut `Microsoft.Office.Tools.Outlook.FormRegionName` dans le fichier de code de zone de formulaire.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Désactiver l’héritage de zone de formulaire
 Par défaut, une classe de message personnalisée hérite de toutes les associations de zones de formulaire de la classe de message de base. Par exemple, une classe de message nommée `IPM.Task.Contoso` dérive de `IPM.Task`. Ainsi, `IPM.Task.Contoso` hérite des associations de zones de formulaire de `IPM.Task`.

 Si vous ne souhaitez pas que la zone de formulaire soit associée aux classes de messages dérivées, affectez la valeur <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> à la propriété **P:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass**. Par exemple, si vous associez une zone de formulaire adjacente à et que vous `IPM.Task` affectez <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> à la propriété la **valeur true**, la zone de formulaire sera ajoutée uniquement au bas d’un formulaire de tâche standard. Elle n’est pas ajoutée à la fin des versions personnalisées d’un formulaire de tâche standard.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Comprendre les types et les noms de classes de messages
 Le nom de type d’un élément Outlook diffère du nom de classe de message d’un élément Outlook. Par exemple, le nom de type d’un élément RSS est `Microsoft.Office.Interop.Outlook.PostItem`. Le nom de classe de message d’un élément RSS est `IPM.Post.RSS`.

 Utilisez le nom de type pour faire référence à un élément Outlook dans le code. Pour obtenir la liste des noms de types, consultez [associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Utilisez le nom de classe de message des éléments Outlook dans l’Assistant **Nouvelle zone de formulaire Outlook** pour associer l’élément à la zone de formulaire. Pour obtenir la liste des noms de classes de messages valides, consultez [associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Concevoir des zones de formulaire adjacentes pour le volet de lecture
 Vous pouvez utiliser le volet de lecture Outlook pour afficher un aperçu d’un élément Outlook sans l’ouvrir. Le volet de lecture est conçu uniquement pour la lecture. Ainsi, les contrôles d’entrée que vous ajoutez à une zone de formulaire adjacente, tels qu’une zone de texte, peuvent ne pas se comporter comme prévu quand l’élément et la zone de formulaire sont ouverts dans le volet de lecture.

 Par exemple, si un élément qui possède une zone de formulaire adjacente est ouvert dans le volet de lecture, la situation suivante est possible :

1. Sélectionnez du texte dans une zone de texte qui se trouve dans la zone de formulaire.

2. Appuyez sur **supprimer**.

3. L’élément de messagerie entier est supprimé, plutôt que le texte de la zone de texte.

   Si vous créez une zone de formulaire adjacente qui contient des contrôles d’entrée, testez les contrôles dans le volet de lecture pour vous assurer qu’ils fonctionnent correctement. Vous pouvez ajouter du code personnalisé qui désactive les contrôles qui ne se comportent pas comme prévu,

   ou encore affecter la valeur <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> à la propriété **P:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead**. Ainsi, la zone de formulaire ne peut pas être utilisée dans le volet de lecture.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> Utiliser des tailles d’icône optimales
 Vous pouvez spécifier les icônes que la zone de formulaire doit afficher en définissant des propriétés d’icônes dans le groupe de propriétés **Icônes** de la fenêtre **Propriétés** . Utilisez les instructions suivantes pour obtenir la meilleure qualité visuelle :

- Pour l’icône **Page** , utilisez un fichier PNG (Portable Network Graphics).

- Les icônes de**Fenêtre** doivent avoir une taille de 32x32 pixels.

- Toutes les autres icônes doivent avoir une taille de 16x16 pixels.

  L’icône **Page** apparaît dans le ruban d’un inspecteur pour les éléments qui ont des zones de formulaire distinctes, de substitution et de remplacement global.

  L’icône de **fenêtre** apparaît dans la zone de notification et dans la boîte de dialogue **ALT** + **Tab** pour les éléments ouverts qui affichent des zones de remplacement ou de remplacement intégral.

## <a name="see-also"></a>Voir aussi
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
