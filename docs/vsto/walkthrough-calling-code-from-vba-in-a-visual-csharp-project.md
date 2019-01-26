---
title: 'Procédure pas à pas : Appeler du code à partir de VBA dans un visuel C# projet'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd968d0c963ae4aa46872bf19e97f357361cf248
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871310"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Procédure pas à pas : Appeler du code à partir de VBA dans un visuel C# projet
  Cette procédure pas à pas montre comment appeler une méthode dans une personnalisation au niveau du document pour Microsoft Office Excel à partir du code VBA (Visual Basic pour Applications) du classeur. Cette procédure comporte trois étapes de base : l'ajout d'une méthode dans la classe d'élément hôte `Sheet1` , l'exposition de la méthode au code VBA dans le classeur, puis l'appel de la méthode à partir du code VBA dans le classeur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement Excel, les concepts présentés ici s'appliquent également aux projets de niveau document pour Word.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un classeur contenant du code VBA  
  
-   Approbation de l'emplacement du classeur à l'aide du Centre de gestion de la confidentialité dans Excel  
  
-   Ajout d'une méthode à la classe d'élément hôte `Sheet1`  
  
-   Extraction d'une interface pour la classe d'élément hôte `Sheet1`  
  
-   Exposition de la méthode au code VBA  
  
-   Appel de la méthode à partir du code VBA  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-a-workbook-that-contains-vba-code"></a>Créer un classeur contenant du code VBA  
 La première étape consiste à créer un classeur prenant en charge les macros et contenant une macro VBA simple. Avant d'exposer le code d'une personnalisation à VBA, le classeur doit déjà contenir du code VBA. Dans le cas contraire, Visual Studio ne peut pas modifier le projet VBA pour permettre au code VBA d'appeler l'assembly de personnalisation.  
  
 Si vous disposez déjà d'un classeur contenant du code VBA que vous souhaitez utiliser, vous pouvez ignorer cette étape.  
  
### <a name="to-create-a-workbook-that-contains-vba-code"></a>Pour créer un classeur contenant du code VBA  
  
1.  Démarrez Excel.  
  
2.  Enregistrer le document actif en tant qu’un **classeur Excel prenant en (\*.xlsm)** portant le nom **ClasseurAvecVBA**. dans un emplacement approprié, tel que le Bureau.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur** .  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, voir [Procédure : Afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **Code** , cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
5.  Dans la fenêtre **Projet** , double-cliquez sur **ThisWorkbook**.  
  
     Le fichier de code de l'objet `ThisWorkbook` s'ouvre.  
  
6.  Ajoutez le code VBA suivant au fichier de code. Ce code définit une fonction simple qui ne fait rien. Le seul objectif de cette fonction consiste à s'assurer qu'un projet VBA existe dans le classeur. Cela est nécessaire pour les étapes ultérieures de cette procédure.  
  
    ```vb  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Enregistrez le document et quittez Excel.  
  
## <a name="create-the-project"></a>Créer le projet  
 Vous pouvez maintenant créer un projet au niveau du document pour Excel qui utilise le classeur prenant en charge les macros que vous avez créé précédemment.  
  
### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** puis **Office/SharePoint**.  
  
4.  Sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez le projet **Classeur Excel 2010** ou **Classeur Excel 2013** .  
  
6.  Dans la zone **Nom** , tapez **AppelCodeDeVBA**.  
  
7.  Cliquez sur **OK**.  
  
     L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8.  Sélectionnez **Copier un document existant**, puis, dans la zone **Chemin d'accès complet du document existant** , spécifiez l'emplacement du classeur **ClasseurAvecVBA** que vous avez créé précédemment. Si vous utilisez votre propre classeur prenant en charge les macros, spécifiez l'emplacement de ce classeur à la place.  
  
9. Cliquez sur **Terminer**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le classeur **ClasseurAvecVBA** dans le concepteur et ajoute le projet **AppelCodeDeVBA** dans l' **Explorateur de solutions**.  
  
## <a name="trust-the-location-of-the-workbook"></a>Faites confiance à l’emplacement du classeur  
 Avant d'exposer le code dans votre solution au code VBA dans le classeur, vous devez approuver VBA dans le classeur à exécuter. Plusieurs méthodes sont possibles. Dans le cas présent, vous allez effectuer cette tâche en approuvant l'emplacement du classeur dans le **Centre de gestion de la confidentialité** d'Excel.  
  
### <a name="to-trust-the-location-of-the-workbook"></a>Pour approuver l'emplacement du classeur  
  
1.  Démarrez Excel.  
  
2.  Cliquez sur l'onglet **Fichier** .  
  
3.  Cliquez sur le bouton **Options Excel** .  
  
4.  Dans le volet des catégories, cliquez sur **Centre de gestion de la confidentialité**.  
  
5.  Dans le volet d'informations, cliquez sur **Paramètres du Centre de gestion de la confidentialité**.  
  
6.  Dans le volet des catégories, cliquez sur **Emplacements approuvés**.  
  
7.  Dans le volet d'informations, cliquez sur **Ajouter un nouvel emplacement**.  
  
8.  Dans la boîte de dialogue **Emplacement approuvé de Microsoft Office** , accédez au dossier qui contient le projet **AppelCodeDeVBA** .  
  
9. Sélectionnez **Les sous-dossiers de cet emplacement sont également approuvés**.  
  
10. Dans la boîte de dialogue **Emplacement approuvé de Microsoft Office** , cliquez sur **OK**.  
  
11. Dans la boîte de dialogue **Centre de gestion de la confidentialité** , cliquez sur **OK**.  
  
12. Dans la boîte de dialogue **Options Excel** , cliquez sur **OK**.  
  
13. Quittez **Excel**.  
  
## <a name="add-a-method-to-the-sheet1-class"></a>Ajoutez une méthode à la classe Sheet1  
 Maintenant que le projet VBA est configuré, ajoutez une méthode publique à la classe d'élément hôte `Sheet1` que vous pouvez appeler à partir du code VBA.  
  
### <a name="to-add-a-method-to-the-sheet1-class"></a>Pour ajouter une méthode à la classe Sheet1  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.cs**, puis cliquez sur **Afficher le code**.  
  
     Le fichier **Sheet1.cs** s'ouvre dans l'éditeur de code.  
  
2.  Ajoutez le code suivant à la classe `Sheet1` . La méthode `CreateVstoNamedRange` crée un nouvel objet <xref:Microsoft.Office.Tools.Excel.NamedRange> au niveau de la plage spécifiée. Cette méthode crée également un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> de <xref:Microsoft.Office.Tools.Excel.NamedRange>. Ultérieurement dans cette procédure, vous appellerez la méthode `CreateVstoNamedRange` à partir du code VBA figurant dans le document.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Ajoutez la méthode suivante à la classe `Sheet1` . Cette méthode remplace la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> pour retourner l'instance actuelle de la classe `Sheet1` .  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Appliquez les attributs suivants avant la première ligne de la déclaration de la classe `Sheet1` . Ces attributs rendent la classe visible pour COM, mais ne génèrent pas d'interface de classe.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extract-an-interface-for-the-sheet1-class"></a>Extraire une interface pour la classe Sheet1  
 Avant d'exposer la méthode `CreateVstoNamedRange` au code VBA, vous devez créer une interface publique qui définit cette méthode et l'exposer à COM.  
  
### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Pour extraire une interface pour la classe Sheet1  
  
1.  Dans le fichier de code **Sheet1.cs** , cliquez n'importe où dans la classe `Sheet1` .  
  
2.  Dans le menu **Refactoriser** , cliquez sur **Extraire l'interface**.  
  
3.  Dans la boîte de dialogue **Extraire l'interface** , dans la zone **Sélectionner des membres publics pour former l'interface** , cliquez sur l'entrée correspondant à la méthode `CreateVstoNamedRange` .  
  
4.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] génère une nouvelle interface nommée `ISheet1`et modifie la définition de la classe `Sheet1` afin d'implémenter l'interface `ISheet1` . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre également le fichier **ISheet1.cs** dans l'éditeur de code.  
  
5.  Dans le fichier **ISheet1.cs** , remplacez la déclaration de l'interface `ISheet1` par le code suivant. Ce code rend publique l'interface `ISheet1` et applique l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> pour rendre l'interface visible par COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Générez le projet.  
  
## <a name="expose-the-method-to-vba-code"></a>Exposition de la méthode au code VBA  
 Pour exposer la méthode `CreateVstoNamedRange` au code VBA dans le classeur, affectez la valeur **True** à la propriété `Sheet1` ReferenceAssemblyFromVbaProject **pour l'élément hôte**.  
  
### <a name="to-expose-the-method-to-vba-code"></a>Pour exposer la méthode au code VBA  
  
1.  Dans l' **Explorateur de solutions**, double-cliquez sur **Sheet1.cs**.  
  
     Le fichier **ClasseurAvecVBA** s'ouvre dans le concepteur et Sheet1 est visible.  
  
2.  Dans la fenêtre **Propriétés** , sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.  
  
3.  Cliquez sur **OK** dans le message qui s'affiche.  
  
4.  Générez le projet.  
  
## <a name="call-the-method-from-vba-code"></a>Appelez la méthode à partir du code VBA  
 Vous pouvez maintenant appeler la méthode `CreateVstoNamedRange` à partir du code VBA figurant dans le classeur.  
  
> [!NOTE]  
>  Dans cette procédure pas à pas, vous allez ajouter du code VBA au classeur lors du débogage du projet. Le code VBA que vous ajoutez à ce document sera remplacé la prochaine fois que vous générerez le projet, car Visual Studio remplace le document dans le dossier de sortie de génération par une copie du document provenant du dossier principal du projet. Si vous souhaitez enregistrer le code VBA, vous pouvez le copier dans le document, dans le dossier du projet. Pour plus d’informations, consultez [combiner de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
### <a name="to-call-the-method-from-vba-code"></a>Pour appeler la méthode à partir du code VBA  
  
1.  Appuyez sur **F5** pour exécuter votre projet.  
  
2.  Sous l'onglet **Développeur** , dans le groupe **Code** , cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
3.  Dans le menu **Insérer** , cliquez sur **Module**.  
  
4.  Ajoutez le code ci-dessous au nouveau module.  
  
     Ce code appelle la méthode `CreateTable` dans l'assembly de personnalisation. La macro accède à cette méthode en utilisant la méthode `GetManagedClass` globale pour accéder à la classe d'élément hôte `Sheet1` que vous avez exposée au code VBA. La méthode `GetManagedClass` a été générée automatiquement quand vous avez défini la propriété **ReferenceAssemblyFromVbaProject** , précédemment dans cette procédure pas à pas.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Appuyez sur **F5**.  
  
6.  Dans le classeur ouvert, cliquez sur la cellule **A1** dans **Feuil1**. Vérifiez que la boîte de message s'affiche.  
  
7.  Quittez Excel sans enregistrer vos modifications.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour en savoir plus sur l'appel de code dans les solutions Office à partir de VBA, consultez les rubriques suivantes :  
  
-   Appeler du code dans un élément hôte dans une personnalisation Visual Basic à partir de VBA. Ce processus est différent du processus Visual C#. Pour plus d’informations, consultez [Procédure pas à pas : Appeler du code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Appeler du code dans un complément VSTO à partir de VBA. Pour plus d’informations, consultez [Procédure pas à pas : Appeler du code dans un complément à VSTO depuis VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Combiner VBA et personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Guide pratique pour Exposer du Code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Guide pratique pour Exposer du Code à VBA dans un Visual C&#35; projet](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Procédure pas à pas : Appeler du code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
