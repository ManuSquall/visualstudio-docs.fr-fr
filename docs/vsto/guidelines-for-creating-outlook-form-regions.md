---
title: "Zones de formulaire de recommandations pour la création d’Outlook | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
ms.assetid: 47ad59d3-5cb7-4d27-a314-9c09937143d7
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e012b9f173e432cfee88beec7d861faaa7be03b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="guidelines-for-creating-outlook-form-regions"></a>Directives pour la création de zones de formulaire Outlook
  Les informations suivantes peuvent vous aider à optimiser vos zones de formulaire et à éviter d’éventuels problèmes :  
  
-   [Utilisation de noms de zones de formulaire](#UsingFormRegions).  
  
-   [Désactivation de l’héritage de zone de formulaire](#DisablingInheritance).  
  
-   [Présentation des types et des noms de classes de messages](#ClassNames).  
  
-   [Conception de zones de formulaire adjacentes pour le volet de lecture](#ReadingPane).  
  
-   [Utilisation de tailles d’icônes optimales](#UsingOptimal).  
  
 Pour plus d’informations sur les zones de formulaire, consultez [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Using Form Region Names  
 Plusieurs noms décrivent la zone de formulaire. Il est important de comprendre la différence entre ces noms et leur impact sur la zone de formulaire. Le tableau suivant décrit chaque nom.  
  
|Nom de zone de formulaire|Description|  
|----------------------|-----------------|  
|Nom d’élément de zone de formulaire|Nom que vous spécifiez pour l’élément **Zone de formulaire Outlook** dans la boîte de dialogue **Ajouter un nouvel élément** . Il s’agit du nom du fichier de code de zone de formulaire affiché dans l’ **Explorateur de solutions**.|  
|Propriété<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> |Vous spécifiez ce nom dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d’affichage** de l’Assistant **Nouvelle zone de formulaire Outlook** . Ce nom apparaît comme propriété **FormRegionName** dans la fenêtre **Propriétés** .<br /><br /> Utilisez la propriété <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> pour spécifier l’étiquette qui identifie la zone de formulaire dans l’interface utilisateur d’Outlook. Pour les zones de formulaire distinctes, ce nom s’affiche sous forme de bouton dans le ruban de l’élément Outlook.<br /><br /> Pour les zones de formulaire adjacentes, ce nom s’affiche sous forme de texte d’en-tête au-dessus de la zone de formulaire.|  
|Attribut Microsoft.Office.Tools.Outlook.FormRegionName|Quand vous ajoutez un élément **Zone de formulaire Outlook** au projet, Visual Studio affecte à cette propriété le nom qualifié complet de la zone de formulaire. Le nom qualifié complet par défaut est le nom du complément VSTO associé au nom de la zone de formulaire par un point, par exemple `OutlookAddIn1.FormRegion1`.<br /><br /> Ce nom qualifié complet apparaît également en tant qu’attribut en haut de la classe de fabrique de zones de formulaire.<br /><br /> Utilisez l’attribut Microsoft.Office.Tools.Outlook.FormRegionName pour identifier de façon unique la zone de formulaire dans tous les composants logiciels Compléments VSTO Outlook. Vous ne pouvez pas modifier la valeur de l’attribut Microsoft.Office.Tools.Outlook.FormRegionName en renommant l’élément de zone de formulaire ou en modifiant le <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriété. Pour modifier ce nom, vous devez modifier l’attribut Microsoft.Office.Tools.Outlook.FormRegionName dans le fichier de code de zone de formulaire.|  
  
##  <a name="DisablingInheritance"></a> Disabling Form Region Inheritance  
 Par défaut, une classe de message personnalisée hérite de toutes les associations de zones de formulaire de la classe de message de base. Par exemple, une classe de message nommée `IPM.Task.Contoso` dérive de gestion intégrée. Tâche. Par conséquent, `IPM.Task.Contoso` hérite des associations de zones de formulaire de gestion intégrée. Tâche.  
  
 Si vous ne souhaitez pas que la zone de formulaire soit associée aux classes de messages dérivées, affectez la valeur <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> à la propriété **P:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass**. Par exemple, si vous associez une zone de formulaire adjacente à gestion intégrée. La tâche et définir le <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propriété **true**, la zone de formulaire est ajoutée uniquement au bas d’un formulaire de tâche standard. Elle n’est pas ajoutée à la fin des versions personnalisées d’un formulaire de tâche standard.  
  
##  <a name="ClassNames"></a> Présentation des types et des noms de classes de messages  
 Le nom de type d’un élément Outlook diffère du nom de classe de message d’un élément Outlook. Par exemple, le nom de type d’un élément RSS est Microsoft.Office.Interop.Outlook.PostItem. Le nom de classe de message d’un élément RSS est gestion intégrée. Post.RSS.  
  
 Utilisez le nom de type pour faire référence à un élément Outlook dans le code. Pour obtenir la liste des noms de types, consultez [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Utilisez le nom de classe de message des éléments Outlook dans l’Assistant **Nouvelle zone de formulaire Outlook** pour associer l’élément à la zone de formulaire. Pour obtenir la liste des noms de classes de messages valides, consultez [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Designing Adjoining Form Regions for the Reading Pane  
 Vous pouvez utiliser le volet de lecture Outlook pour afficher un aperçu d’un élément Outlook sans l’ouvrir. Le volet de lecture est conçu uniquement pour la lecture. Ainsi, les contrôles d’entrée que vous ajoutez à une zone de formulaire adjacente, tels qu’une zone de texte, peuvent ne pas se comporter comme prévu quand l’élément et la zone de formulaire sont ouverts dans le volet de lecture.  
  
 Par exemple, si un élément qui possède une zone de formulaire adjacente est ouvert dans le volet de lecture, la situation suivante est possible :  
  
1.  Sélectionnez du texte dans une zone de texte qui se trouve dans la zone de formulaire.  
  
2.  Appuyez sur la touche Suppr.  
  
3.  L’élément de messagerie entier est supprimé, plutôt que le texte de la zone de texte.  
  
 Si vous créez une zone de formulaire adjacente qui contient des contrôles d’entrée, testez les contrôles dans le volet de lecture pour vous assurer qu’ils fonctionnent correctement. Vous pouvez ajouter du code personnalisé qui désactive les contrôles qui ne se comportent pas comme prévu,  
  
 ou encore affecter la valeur <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> à la propriété **P:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead**. Ainsi, la zone de formulaire ne peut pas être utilisée dans le volet de lecture.  
  
##  <a name="UsingOptimal"></a> Using Optimal Icon Sizes  
 Vous pouvez spécifier les icônes que la zone de formulaire doit afficher en définissant des propriétés d’icônes dans le groupe de propriétés **Icônes** de la fenêtre **Propriétés** . Utilisez les instructions suivantes pour obtenir la meilleure qualité visuelle :  
  
-   Pour l’icône **Page** , utilisez un fichier PNG (Portable Network Graphics).  
  
-   Les icônes de**Fenêtre** doivent avoir une taille de 32x32 pixels.  
  
-   Toutes les autres icônes doivent avoir une taille de 16x16 pixels.  
  
 L’icône **Page** apparaît dans le ruban d’un inspecteur pour les éléments qui ont des zones de formulaire distinctes, de substitution et de remplacement global.  
  
 L’icône **Fenêtre** est affichée dans la zone de notification et dans la boîte de dialogue Alt+Tab pour les éléments ouverts qui affichent des zones de substitution ou de remplacement global.  
  
## <a name="see-also"></a>Voir aussi  
 [L’accès à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Association d’une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  