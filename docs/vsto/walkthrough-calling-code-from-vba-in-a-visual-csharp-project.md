---
title: "Proc&#233;dure pas &#224; pas&#160;: appel de code &#224; partir de VBA dans un projet Visual&#160;C# | Microsoft Docs"
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
  - "Excel (développement Office dans Visual Studio), appel de code depuis VBA"
  - "Word (développement Office dans Visual Studio), appel de code depuis VBA"
  - "Visual C# (développement Office dans Visual Studio), appel de code depuis VBA"
  - "classeurs (développement Office dans Visual Studio), appel de code depuis VBA"
  - "VBA (développement Office dans Visual Studio), appel de code dans les personnalisations au niveau du document"
  - "documents Office (développement Office dans Visual Studio), Visual Basic pour Applications"
  - "appeler du code à partir de VBA"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), appel de code"
ms.assetid: 9a5741f1-8260-4964-afa1-c69b68d1cfdf
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: appel de code &#224; partir de VBA dans un projet Visual&#160;C# #
  Cette procédure pas à pas montre comment appeler une méthode dans une personnalisation au niveau du document pour Microsoft Office Excel à partir du code VBA \(Visual Basic pour Applications\) du classeur. Cette procédure comporte trois étapes de base : l'ajout d'une méthode dans la classe d'élément hôte `Sheet1`, l'exposition de la méthode au code VBA dans le classeur, puis l'appel de la méthode à partir du code VBA dans le classeur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement Excel, les concepts présentés ici s'appliquent également aux projets de niveau document pour Word.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un classeur contenant du code VBA  
  
-   Approbation de l'emplacement du classeur à l'aide du Centre de gestion de la confidentialité dans Excel  
  
-   Ajout d'une méthode à la classe d'élément hôte `Sheet1`  
  
-   Extraction d'une interface pour la classe d'élément hôte `Sheet1`  
  
-   Exposition de la méthode au code VBA  
  
-   Appel de la méthode à partir du code VBA  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Création d'un classeur contenant du code VBA  
 La première étape consiste à créer un classeur prenant en charge les macros et contenant une macro VBA simple. Avant d'exposer le code d'une personnalisation à VBA, le classeur doit déjà contenir du code VBA. Dans le cas contraire, Visual Studio ne peut pas modifier le projet VBA pour permettre au code VBA d'appeler l'assembly de personnalisation.  
  
 Si vous disposez déjà d'un classeur contenant du code VBA que vous souhaitez utiliser, vous pouvez ignorer cette étape.  
  
#### Pour créer un classeur contenant du code VBA  
  
1.  Démarrez Excel.  
  
2.  Enregistrez le document actif en tant que **Classeur Excel \(prenant en charge les macros\) \(\*.xlsm\)** sous le nom **ClasseurAvecVBA** dans un emplacement approprié, tel que le Bureau.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **Code**, cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
5.  Dans la fenêtre **Projet**, double\-cliquez sur **ThisWorkbook**.  
  
     Le fichier de code de l'objet `ThisWorkbook` s'ouvre.  
  
6.  Ajoutez le code VBA suivant au fichier de code. Ce code définit une fonction simple qui ne fait rien. Le seul objectif de cette fonction consiste à s'assurer qu'un projet VBA existe dans le classeur. Cela est nécessaire pour les étapes ultérieures de cette procédure.  
  
    ```  
    Sub EmptySub() End Sub  
    ```  
  
7.  Enregistrez le document et quittez Excel.  
  
## Création du projet  
 Vous pouvez maintenant créer un projet au niveau du document pour Excel qui utilise le classeur prenant en charge les macros que vous avez créé précédemment.  
  
#### Pour créer un projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C\#** puis **Office\/SharePoint**.  
  
4.  Sélectionnez le nœud **Compléments Office**.  
  
5.  Dans la liste des modèles de projet, sélectionnez le projet **Classeur Excel 2010** ou **Classeur Excel 2013**.  
  
6.  Dans la zone **Nom**, tapez **AppelCodeDeVBA**.  
  
7.  Cliquez sur **OK**.  
  
     L'**Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8.  Sélectionnez **Copier un document existant**, puis, dans la zone **Chemin d'accès complet du document existant**, spécifiez l'emplacement du classeur **ClasseurAvecVBA** que vous avez créé précédemment. Si vous utilisez votre propre classeur prenant en charge les macros, spécifiez l'emplacement de ce classeur à la place.  
  
9. Cliquez sur **Terminer**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le classeur **ClasseurAvecVBA** dans le concepteur et ajoute le projet **AppelCodeDeVBA** dans l'**Explorateur de solutions**.  
  
## Approbation de l'emplacement du classeur  
 Avant d'exposer le code dans votre solution au code VBA dans le classeur, vous devez approuver VBA dans le classeur à exécuter. Plusieurs méthodes sont possibles. Dans le cas présent, vous allez effectuer cette tâche en approuvant l'emplacement du classeur dans le **Centre de gestion de la confidentialité** d'Excel.  
  
#### Pour approuver l'emplacement du classeur  
  
1.  Démarrez Excel.  
  
2.  Cliquez sur l'onglet **Fichier**.  
  
3.  Cliquez sur le bouton **Options Excel**.  
  
4.  Dans le volet des catégories, cliquez sur **Centre de gestion de la confidentialité**.  
  
5.  Dans le volet d'informations, cliquez sur **Paramètres du Centre de gestion de la confidentialité**.  
  
6.  Dans le volet des catégories, cliquez sur **Emplacements approuvés**.  
  
7.  Dans le volet d'informations, cliquez sur **Ajouter un nouvel emplacement**.  
  
8.  Dans la boîte de dialogue **Emplacement approuvé de Microsoft Office**, accédez au dossier qui contient le projet **AppelCodeDeVBA**.  
  
9. Sélectionnez **Les sous\-dossiers de cet emplacement sont également approuvés**.  
  
10. Dans la boîte de dialogue **Emplacement approuvé de Microsoft Office**, cliquez sur **OK**.  
  
11. Dans la boîte de dialogue **Centre de gestion de la confidentialité**, cliquez sur **OK**.  
  
12. Dans la boîte de dialogue **Options Excel**, cliquez sur **OK**.  
  
13. Quittez **Excel**.  
  
## Ajout d'une méthode à la classe Sheet1  
 Maintenant que le projet VBA est configuré, ajoutez une méthode publique à la classe d'élément hôte `Sheet1` que vous pouvez appeler à partir du code VBA.  
  
#### Pour ajouter une méthode à la classe Sheet1  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.cs**, puis cliquez sur **Afficher le code**.  
  
     Le fichier **Sheet1.cs** s'ouvre dans l'éditeur de code.  
  
2.  Ajoutez le code suivant à la classe `Sheet1`. La méthode `CreateVstoNamedRange` crée un nouvel objet <xref:Microsoft.Office.Tools.Excel.NamedRange> au niveau de la plage spécifiée. Cette méthode crée également un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> de <xref:Microsoft.Office.Tools.Excel.NamedRange>. Ultérieurement dans cette procédure, vous appellerez la méthode `CreateVstoNamedRange` à partir du code VBA figurant dans le document.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/Sheet1.cs#2)]  
  
3.  Ajoutez la méthode suivante à la classe `Sheet1`. Cette méthode remplace la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> pour retourner l'instance actuelle de la classe `Sheet1`.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/Sheet1.cs#3)]  
  
4.  Appliquez les attributs suivants avant la première ligne de la déclaration de la classe `Sheet1`. Ces attributs rendent la classe visible pour COM, mais ne génèrent pas d'interface de classe.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/Sheet1.cs#1)]  
  
## Extraction d'une interface pour la classe Sheet1  
 Avant d'exposer la méthode `CreateVstoNamedRange` au code VBA, vous devez créer une interface publique qui définit cette méthode et l'exposer à COM.  
  
#### Pour extraire une interface pour la classe Sheet1  
  
1.  Dans le fichier de code **Sheet1.cs**, cliquez n'importe où dans la classe `Sheet1`.  
  
2.  Dans le menu **Refactoriser**, cliquez sur **Extraire l'interface**.  
  
3.  Dans la boîte de dialogue **Extraire l'interface**, dans la zone **Sélectionner des membres publics pour former l'interface**, cliquez sur l'entrée correspondant à la méthode `CreateVstoNamedRange`.  
  
4.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] génère une nouvelle interface nommée `ISheet1` et modifie la définition de la classe `Sheet1` afin d'implémenter l'interface `ISheet1`.[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre également le fichier **ISheet1.cs** dans l'éditeur de code.  
  
5.  Dans le fichier **ISheet1.cs**, remplacez la déclaration de l'interface `ISheet1` par le code suivant. Ce code rend publique l'interface `ISheet1` et applique l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> pour rendre l'interface visible par COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/ISheet1.cs#4)]  
  
6.  Générez le projet.  
  
## Exposition de la méthode au code VBA  
 Pour exposer la méthode `CreateVstoNamedRange` au code VBA dans le classeur, affectez la valeur **True** à la propriété **ReferenceAssemblyFromVbaProject** pour l'élément hôte `Sheet1`.  
  
#### Pour exposer la méthode au code VBA  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur **Sheet1.cs**.  
  
     Le fichier **ClasseurAvecVBA** s'ouvre dans le concepteur et Sheet1 est visible.  
  
2.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.  
  
3.  Cliquez sur **OK** dans le message qui s'affiche.  
  
4.  Générez le projet.  
  
## Appel de la méthode à partir du code VBA  
 Vous pouvez maintenant appeler la méthode `CreateVstoNamedRange` à partir du code VBA figurant dans le classeur.  
  
> [!NOTE]  
>  Dans cette procédure pas à pas, vous allez ajouter du code VBA au classeur lors du débogage du projet. Le code VBA que vous ajoutez à ce document sera remplacé la prochaine fois que vous générerez le projet, car Visual Studio remplace le document dans le dossier de sortie de génération par une copie du document provenant du dossier principal du projet. Si vous souhaitez enregistrer le code VBA, vous pouvez le copier dans le document, dans le dossier du projet. Pour plus d'informations, consultez [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### Pour appeler la méthode à partir du code VBA  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sous l'onglet **Développeur**, dans le groupe **Code**, cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
3.  Dans le menu **Insérer**, cliquez sur **Module**.  
  
4.  Ajoutez le code ci\-dessous au nouveau module.  
  
     Ce code appelle la méthode `CreateTable` dans l'assembly de personnalisation. La macro accède à cette méthode en utilisant la méthode `GetManagedClass` globale pour accéder à la classe d'élément hôte `Sheet1` que vous avez exposée au code VBA. La méthode `GetManagedClass` a été générée automatiquement quand vous avez défini la propriété **ReferenceAssemblyFromVbaProject**, précédemment dans cette procédure pas à pas.  
  
    ```  
    Sub CallVSTOMethod() Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1 Set VSTOSheet1 = GetManagedClass(Sheet1) Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange") End Sub  
    ```  
  
5.  Appuyez sur F5.  
  
6.  Dans le classeur ouvert, cliquez sur la cellule **A1** dans **Feuil1**. Vérifiez que la boîte de message s'affiche.  
  
7.  Quittez Excel sans enregistrer vos modifications.  
  
## Étapes suivantes  
 Pour en savoir plus sur l'appel de code dans les solutions Office à partir de VBA, consultez les rubriques suivantes :  
  
-   Appeler du code dans un élément hôte dans une personnalisation Visual Basic à partir de VBA. Ce processus est différent du processus Visual C\#. Pour plus d'informations, consultez [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Appeler du code dans un complément VSTO à partir de VBA. Pour plus d'informations, consultez [Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## Voir aussi  
 [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Comment : exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Comment : exposer du code à VBA dans un projet Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  
  