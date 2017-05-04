---
title: "Acc&#232;s &#224; une zone de formulaire au moment de l&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "inspecteurs (développement Office dans Visual Studio)"
  - "Explorateurs (développement Office dans Visual Studio)"
  - "zones de formulaire (développement Office dans Visual Studio), accès au moment de l’exécution"
ms.assetid: 58eaa9e0-acba-4a13-a6dd-b7e37a38156e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Acc&#232;s &#224; une zone de formulaire au moment de l&#39;ex&#233;cution
  
  
|S'applique à|  
|------------------|  
|Les informations de cette rubrique s'appliquent uniquement aux types de projets et aux versions de Microsoft Office indiqués ci\-dessous. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Type de projet**<br /><br /> -   Projets de complément VSTO<br /><br /> **Version de Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Utilisez la classe `Globals` pour accéder aux zones de formulaire depuis n’importe où dans votre projet Outlook. Pour plus d'informations sur la classe `Globals`, consultez [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Accès aux zones de formulaire qui s’affichent dans une fenêtre d’inspecteur Outlook spécifique  
 Pour accéder à toutes les zones de formulaire qui s’affichent dans un inspecteur Outlook spécifique, appelez la propriété `FormRegions` de la classe `Globals` et passez un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> qui représente l’inspecteur.  
  
 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans l’inspecteur qui a actuellement le focus. Cet exemple accède ensuite à une zone de formulaire de la collection nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_Outlook_FR_Access#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#2)]  
  
## Accès aux zones de formulaire qui s’affichent dans une fenêtre d’explorateur Outlook spécifique  
 Pour accéder à toutes les zones de formulaire qui s’affichent dans un explorateur Outlook spécifique, appelez la propriété `FormRegions` de la classe `Globals` et passez un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> qui représente l’explorateur.  
  
 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans l’explorateur qui a actuellement le focus. Cet exemple accède ensuite à une zone de formulaire de la collection nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#3)]
 [!code-vb[Trin_Outlook_FR_Access#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#3)]  
  
## Accès à toutes les zones de formulaire  
 Pour accéder à toutes les zones de formulaire qui s’affichent dans tous les explorateurs et tous les inspecteurs, appelez la propriété `FormRegions` de la classe `Globals`.  
  
 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans tous les explorateurs et tous les inspecteurs. Cet exemple accède ensuite à une zone de formulaire nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Outlook_FR_Access#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#1)]  
  
## Accès aux contrôles d’une zone de formulaire  
 Pour accéder aux contrôles d’une zone de formulaire à l’aide de la classe `Globals`, vous devez rendre les contrôles accessibles au code en dehors du fichier de code de la zone de formulaire.  
  
### Zones de formulaire conçues dans le Concepteur de zones de formulaire  
 En C\#, modifiez le modificateur de chaque contrôle auquel vous voulez accéder. Pour cela, sélectionnez chaque contrôle dans le Concepteur de zones de formulaire et modifiez la propriété **Modifiers** sur **Interne** ou **public** dans la fenêtre **Propriétés**. Par exemple, si vous affectez à la propriété **Modifiers** de `textBox1` la valeur **Interne**, vous pouvez accéder à `textBox1` en tapant `Globals.FormRegions.FormRegion1.textBox1`.  
  
 En Visual Basic, il est inutile de modifier le modificateur.  
  
### Zones de formulaire importées  
 Quand vous importez une zone de formulaire conçue dans Outlook, le modificateur d’accès de chaque contrôle de la zone de formulaire devient privé. Puisque vous ne pouvez pas utiliser le Concepteur de zones de formulaire pour modifier une zone de formulaire importée, il n’existe aucun moyen de modifier le modificateur d’un contrôle dans la fenêtre **Propriétés**.  
  
 Pour activer l’accès à un contrôle en dehors du fichier de code de la zone de formulaire, créez une propriété dans ce fichier de code pour retourner ce contrôle.  
  
 Pour plus d’informations sur la création de propriétés en C\#, consultez [Comment : déclarer et utiliser des propriétés en lecture-écriture &#40;Guide de programmation C&#35;&#41;](http://msdn.microsoft.com/library/a4962fef-af7e-4c4b-a929-4ae4d646ab8a).  
  
 Pour plus d’informations sur la création de propriétés en Visual Basic, consultez [PAS DANS LA BUILD : Comment : ajouter des champs et des propriétés à une classe](http://msdn.microsoft.com/fr-fr/ae53f61b-3abc-413e-8931-703c5f5e8fc2).  
  
## Voir aussi  
 [Directives pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Association d'une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Procédure pas à pas : importation d'une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Comment : empêcher Outlook d'afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  