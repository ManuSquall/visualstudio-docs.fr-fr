---
title: Accéder à une zone de formulaire au moment de l’exécution
description: Découvrez comment accéder à une zone de formulaire dans différents types de projets et versions de Microsoft Office au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbd60f5773392af2066e4693751dd6fff99128b9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827966"
---
# <a name="access-a-form-region-at-run-time"></a>Accéder à une zone de formulaire au moment de l’exécution

|S’applique à|
|----------------|
|Les informations de cette rubrique s'appliquent uniquement aux types de projets et aux versions de Microsoft Office indiqués ci-dessous. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Type de projet**<br /><br /> -Projets de complément VSTO<br /><br /> **Version de Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Utilisez la classe `Globals` pour accéder aux zones de formulaire depuis n’importe où dans votre projet Outlook. Pour plus d’informations sur la `Globals` classe, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Accéder aux zones de formulaire qui s’affichent dans une fenêtre d’inspecteur Outlook spécifique
 Pour accéder à toutes les zones de formulaire qui s’affichent dans un inspecteur Outlook spécifique, appelez la propriété `FormRegions` de la classe `Globals` et passez un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> qui représente l’inspecteur.

 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans l’inspecteur qui a actuellement le focus. Cet exemple accède ensuite à une zone de formulaire de la collection nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet2":::

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Accéder aux zones de formulaire qui s’affichent dans une fenêtre d’explorateur Outlook spécifique
 Pour accéder à toutes les zones de formulaire qui s’affichent dans un explorateur Outlook spécifique, appelez la propriété `FormRegions` de la classe `Globals` et passez un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> qui représente l’explorateur.

 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans l’explorateur qui a actuellement le focus. Cet exemple accède ensuite à une zone de formulaire de la collection nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet3":::

## <a name="access-all-form-regions"></a>Accéder à toutes les zones de formulaire
 Pour accéder à toutes les zones de formulaire qui s’affichent dans tous les explorateurs et tous les inspecteurs, appelez la propriété `FormRegions` de la classe `Globals` .

 L’exemple suivant obtient la collection des zones de formulaire qui s’affichent dans tous les explorateurs et tous les inspecteurs. Cet exemple accède ensuite à une zone de formulaire nommée `formRegion1` et définit le texte qui apparaît dans une zone de texte sur `Hello World`.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet1":::

## <a name="access-controls-on-a-form-region"></a>Contrôles d’accès sur une zone de formulaire
 Pour accéder aux contrôles d’une zone de formulaire à l’aide de la classe `Globals` , vous devez rendre les contrôles accessibles au code en dehors du fichier de code de la zone de formulaire.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Zones de formulaire conçues dans le concepteur de zones de formulaire
 En C#, modifiez le modificateur de chaque contrôle auquel vous voulez accéder. Pour cela, sélectionnez chaque contrôle dans le Concepteur de zones de formulaire et modifiez la propriété **Modifiers** sur **Interne** ou **public** dans la fenêtre **Propriétés** . Par exemple, si vous affectez à la propriété **Modifiers** de `textBox1` la valeur **Interne**, vous pouvez accéder à `textBox1` en tapant `Globals.FormRegions.FormRegion1.textBox1`.

 En Visual Basic, il est inutile de modifier le modificateur.

### <a name="imported-form-regions"></a>Zones de formulaire importées
 Quand vous importez une zone de formulaire conçue dans Outlook, le modificateur d’accès de chaque contrôle de la zone de formulaire devient privé. Puisque vous ne pouvez pas utiliser le Concepteur de zones de formulaire pour modifier une zone de formulaire importée, il n’existe aucun moyen de modifier le modificateur d’un contrôle dans la fenêtre **Propriétés** .

 Pour activer l’accès à un contrôle en dehors du fichier de code de la zone de formulaire, créez une propriété dans ce fichier de code pour retourner ce contrôle.

 Pour plus d’informations sur la création de propriétés en C#, consultez [Guide pratique pour déclarer et utiliser les propriétés en lecture/écriture &#40;Guide de programmation du&#35; C&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Pour plus d’informations sur la création de propriétés dans Visual Basic, consultez [How to : Create a Property (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Voir aussi
- [Instructions pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
