---
title: Accéder à une zone de formulaire lors de l’exécution
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c0cdea460b2a50819aff3c300b8510ffd577c8f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="access-a-form-region-at-runtime"></a>Accéder à une zone de formulaire lors de l’exécution

|S'applique à|  
|----------------|  
|Les informations de cette rubrique s'appliquent uniquement aux types de projets et aux versions de Microsoft Office indiqués ci-dessous. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Type de projet**<br /><br /> -Projets de complément VSTO<br /><br /> **Version de Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Utilisez la classe `Globals` pour accéder aux zones de formulaire depuis n’importe où dans votre projet Outlook. Pour plus d’informations sur la `Globals` de classe, consultez [d’accès Global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Zones de formulaire d’accès qui s’affichent dans une fenêtre d’inspecteur Outlook spécifique  
 Pour accéder à toutes les zones de formulaire qui s’affichent dans un inspecteur Outlook spécifique, appelez la propriété `FormRegions` de la classe `Globals` et passez un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> qui représente l’inspecteur.  

 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans l’inspecteur qui a actuellement le focus. Cet exemple accède ensuite à une zone de formulaire de la collection nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Zones de formulaire d’accès qui s’affichent dans une fenêtre d’Explorateur Outlook spécifique  
 Pour accéder à toutes les zones de formulaire qui s’affichent dans un explorateur Outlook spécifique, appelez la propriété `FormRegions` de la classe `Globals` et passez un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> qui représente l’explorateur.  

 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans l’explorateur qui a actuellement le focus. Cet exemple accède ensuite à une zone de formulaire de la collection nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="access-all-form-regions"></a>Accéder à toutes les zones de formulaire  
 Pour accéder à toutes les zones de formulaire qui s’affichent dans tous les explorateurs et tous les inspecteurs, appelez la propriété `FormRegions` de la classe `Globals` .  

 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans tous les explorateurs et tous les inspecteurs. Cet exemple accède ensuite à une zone de formulaire nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="access-controls-on-a-form-region"></a>Contrôles d’accès sur une zone de formulaire  
 Pour accéder aux contrôles d’une zone de formulaire à l’aide de la classe `Globals` , vous devez rendre les contrôles accessibles au code en dehors du fichier de code de la zone de formulaire.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Zones de formulaire conçues dans le Concepteur de zones de formulaire  
 En C#, modifiez le modificateur de chaque contrôle auquel vous voulez accéder. Pour cela, sélectionnez chaque contrôle dans le Concepteur de zones de formulaire et modifiez la propriété **Modifiers** sur **Interne** ou **public** dans la fenêtre **Propriétés** . Par exemple, si vous affectez à la propriété **Modifiers** de `textBox1` la valeur **Interne**, vous pouvez accéder à `textBox1` en tapant `Globals.FormRegions.FormRegion1.textBox1`.  

 En Visual Basic, il est inutile de modifier le modificateur.  

### <a name="imported-form-regions"></a>Zones de formulaire importées  
 Quand vous importez une zone de formulaire conçue dans Outlook, le modificateur d’accès de chaque contrôle de la zone de formulaire devient privé. Puisque vous ne pouvez pas utiliser le Concepteur de zones de formulaire pour modifier une zone de formulaire importée, il n’existe aucun moyen de modifier le modificateur d’un contrôle dans la fenêtre **Propriétés** .  

 Pour activer l’accès à un contrôle en dehors du fichier de code de la zone de formulaire, créez une propriété dans ce fichier de code pour retourner ce contrôle.  

 Pour plus d’informations sur la création de propriétés en c#, consultez [Comment : déclarer et utiliser lire écrire des propriétés &#40;C&#35; guide de programmation&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Pour plus d’informations sur la création de propriétés en Visual Basic, consultez [Comment : créer une propriété (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Voir aussi  
 [Recommandations pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procédure pas à pas : Conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Procédure pas à pas : Importation d’une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)  
