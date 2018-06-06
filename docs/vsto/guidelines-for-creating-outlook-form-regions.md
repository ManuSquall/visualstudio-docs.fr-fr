---
title: Recommandations pour la création de zones de formulaire Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dfbe02c652c53f0b7e5b2322ce76e7c022487d2e
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Recommandations pour créer des zones de formulaire Outlook
  Les informations suivantes peuvent vous aider à optimiser vos zones de formulaire et à éviter d’éventuels problèmes :  
  
-   [Utilisez des noms de région de formulaire](#UsingFormRegions).  
  
-   [Désactiver l’héritage de zone de formulaire](#DisablingInheritance).  
  
-   [Comprendre les types et les noms de classe de message](#ClassNames).  
  
-   [Conception du volet de lecture, les zones de formulaire adjacentes](#ReadingPane).  
  
-   [Utiliser les tailles d’icônes optimales](#UsingOptimal).  
  
 Pour plus d’informations sur les zones de formulaire, consultez [zones de formulaire Outlook de créer](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Utilisez des noms de région de formulaire  
 Plusieurs noms décrivent la zone de formulaire. Il est important de comprendre la différence entre ces noms et leur impact sur la zone de formulaire. Le tableau suivant décrit chaque nom.  
  
|Nom de zone de formulaire|Description|  
|----------------------|-----------------|  
|Nom d’élément de zone de formulaire|Nom que vous spécifiez pour l’élément **Zone de formulaire Outlook** dans la boîte de dialogue **Ajouter un nouvel élément** . Il s’agit du nom du fichier de code de zone de formulaire affiché dans l’ **Explorateur de solutions**.|  
|Propriété<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> |Vous spécifiez ce nom dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d’affichage** de l’Assistant **Nouvelle zone de formulaire Outlook** . Ce nom apparaît comme propriété **FormRegionName** dans la fenêtre **Propriétés** .<br /><br /> Utilisez la propriété <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> pour spécifier l’étiquette qui identifie la zone de formulaire dans l’interface utilisateur d’Outlook. Pour les zones de formulaire distinctes, ce nom s’affiche sous forme de bouton dans le ruban de l’élément Outlook.<br /><br /> Pour les zones de formulaire adjacentes, ce nom s’affiche sous forme de texte d’en-tête au-dessus de la zone de formulaire.|  
|Attribut `Microsoft.Office.Tools.Outlook.FormRegionName`|Quand vous ajoutez un élément **Zone de formulaire Outlook** au projet, Visual Studio affecte à cette propriété le nom qualifié complet de la zone de formulaire. Le nom qualifié complet par défaut est le nom du complément VSTO associé au nom de la zone de formulaire par un point, par exemple `OutlookAddIn1.FormRegion1`.<br /><br /> Ce nom qualifié complet apparaît également en tant qu’attribut en haut de la classe de fabrique de zones de formulaire.<br /><br /> Utilisez le `Microsoft.Office.Tools.Outlook.FormRegionName` pour identifier de façon unique la zone de formulaire dans les Compléments VSTO Outlook tous les attributs. Vous ne pouvez pas modifier la valeur de la `Microsoft.Office.Tools.Outlook.FormRegionName` attribut en renommant l’élément de zone de formulaire ou en modifiant le <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriété. Pour modifier ce nom, vous devez modifier le `Microsoft.Office.Tools.Outlook.FormRegionName` attribut dans le fichier de code de zone de formulaire.|  
  
##  <a name="DisablingInheritance"></a> Désactiver l’héritage de zone de formulaire  
 Par défaut, une classe de message personnalisée hérite de toutes les associations de zones de formulaire de la classe de message de base. Par exemple, une classe de message nommée `IPM.Task.Contoso` dérive `IPM.Task`. Par conséquent, `IPM.Task.Contoso` hérite des associations de zones de formulaire de `IPM.Task`.  
  
 Si vous ne souhaitez pas que la zone de formulaire soit associée aux classes de messages dérivées, affectez la valeur <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> à la propriété **P:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass**. Par exemple, si vous associez une zone de formulaire adjacente à `IPM.Task` et définir le <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propriété **true**, la zone de formulaire est ajoutée uniquement au bas d’un formulaire de tâche standard. Elle n’est pas ajoutée à la fin des versions personnalisées d’un formulaire de tâche standard.  
  
##  <a name="ClassNames"></a> Comprendre les types et les noms de classe de message  
 Le nom de type d’un élément Outlook diffère du nom de classe de message d’un élément Outlook. Par exemple, le nom de type d’un élément RSS est `Microsoft.Office.Interop.Outlook.PostItem`. Le nom de classe de message d’un élément RSS est `IPM.Post.RSS`.  
  
 Utilisez le nom de type pour faire référence à un élément Outlook dans le code. Pour obtenir la liste des noms de type, consultez [associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Utilisez le nom de classe de message des éléments Outlook dans l’Assistant **Nouvelle zone de formulaire Outlook** pour associer l’élément à la zone de formulaire. Pour obtenir la liste des noms de classe de message valides, consultez [associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Conception de zones de formulaire adjacentes pour le volet de lecture  
 Vous pouvez utiliser le volet de lecture Outlook pour afficher un aperçu d’un élément Outlook sans l’ouvrir. Le volet de lecture est conçu uniquement pour la lecture. Ainsi, les contrôles d’entrée que vous ajoutez à une zone de formulaire adjacente, tels qu’une zone de texte, peuvent ne pas se comporter comme prévu quand l’élément et la zone de formulaire sont ouverts dans le volet de lecture.  
  
 Par exemple, si un élément qui possède une zone de formulaire adjacente est ouvert dans le volet de lecture, la situation suivante est possible :  
  
1.  Sélectionnez du texte dans une zone de texte qui se trouve dans la zone de formulaire.  
  
2.  Appuyez sur **supprimer**.  
  
3.  L’élément de messagerie entier est supprimé, plutôt que le texte de la zone de texte.  
  
 Si vous créez une zone de formulaire adjacente qui contient des contrôles d’entrée, testez les contrôles dans le volet de lecture pour vous assurer qu’ils fonctionnent correctement. Vous pouvez ajouter du code personnalisé qui désactive les contrôles qui ne se comportent pas comme prévu,  
  
 ou encore affecter la valeur <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> à la propriété **P:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead**. Ainsi, la zone de formulaire ne peut pas être utilisée dans le volet de lecture.  
  
##  <a name="UsingOptimal"></a> Utiliser les tailles d’icônes optimales  
 Vous pouvez spécifier les icônes que la zone de formulaire doit afficher en définissant des propriétés d’icônes dans le groupe de propriétés **Icônes** de la fenêtre **Propriétés** . Utilisez les instructions suivantes pour obtenir la meilleure qualité visuelle :  
  
-   Pour l’icône **Page** , utilisez un fichier PNG (Portable Network Graphics).  
  
-   Les icônes de**Fenêtre** doivent avoir une taille de 32x32 pixels.  
  
-   Toutes les autres icônes doivent avoir une taille de 16x16 pixels.  
  
 L’icône **Page** apparaît dans le ruban d’un inspecteur pour les éléments qui ont des zones de formulaire distinctes, de substitution et de remplacement global.  
  
 Le **fenêtre** icône s’affiche dans la zone de notification et dans le **Alt**+**onglet** ce remplacement de l’affichage ou le remplacement des éléments de boîte de dialogue Ouvrir régions.  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder à une zone de formulaire lors de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  