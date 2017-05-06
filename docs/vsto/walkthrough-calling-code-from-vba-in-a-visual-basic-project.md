---
title: "Proc&#233;dure pas &#224; pas&#160;: appel de code &#224; partir de VBA dans un projet Visual Basic"
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
  - "documents (développement Office dans Visual Studio), et Visual Basic pour Applications"
  - "ThisDocument (classe)"
  - "Word (développement Office dans Visual Studio), appel de code depuis VBA"
  - "Visual Basic (développement Office dans Visual Studio), appel du code à partir de VBA"
  - "VBA (développement Office dans Visual Studio), appel de code dans les personnalisations au niveau du document"
  - "documents Office (développement Office dans Visual Studio), Visual Basic pour Applications"
  - "appeler du code à partir de VBA"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), appel de code"
ms.assetid: 798bc2fa-449e-4d1a-86b4-18e57b02a4a8
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Proc&#233;dure pas &#224; pas&#160;: appel de code &#224; partir de VBA dans un projet Visual Basic
  Cette procédure pas à pas montre comment appeler une méthode dans une personnalisation au niveau du document pour Microsoft Office Word à partir d'un code VBA \(Visual Basic pour Applications\) dans le document. Cette procédure comporte trois étapes de base : l'ajout d'une méthode dans la classe d'élément hôte `ThisDocument`, l'exposition de la méthode au code VBA, puis l'appel de la méthode à partir du code VBA dans le document.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement Word, les concepts présentés ici s'appliquent également aux projets de niveau document pour Excel.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un document contenant du code VBA.  
  
-   Approbation de l'emplacement du document à l'aide du Centre de gestion de la confidentialité dans Word.  
  
-   Ajout d'une méthode à la classe d'élément hôte `ThisDocument`.  
  
-   Exposition de la méthode au code VBA.  
  
-   Appel de la méthode à partir du code VBA  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Création d'un document contenant du code VBA  
 La première étape consiste à créer un document prenant en charge les macros et contenant une macro VBA simple. Le document doit contenir un projet VBA avant que vous créiez un projet Visual Studio basé sur ce document. Dans le cas contraire, Visual Studio ne peut pas modifier le projet VBA pour permettre au code VBA d'appeler dans l'assembly de personnalisation.  
  
 Si vous disposez déjà d'un document contenant du code VBA que vous souhaitez utiliser, vous pouvez ignorer cette étape.  
  
#### Pour créer un document contenant du code VBA  
  
1.  Démarrez Word.  
  
2.  Enregistrez le document actif en tant que **Document prenant en charge les macros \(\*.docm\)** avec le nom **DocumentAvecVBA**. Enregistrez\-le dans un emplacement approprié, tel que le Bureau.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **Code**, cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
5.  Dans la fenêtre **Projet**, double\-cliquez sur **ThisDocument**.  
  
     Le fichier de code de l'objet `ThisDocument` s'ouvre.  
  
6.  Ajoutez le code VBA suivant au fichier de code. Ce code définit une fonction simple qui ne fait rien. Le seul objectif de cette fonction consiste à s'assurer qu'un projet VBA existe dans le document. Cela est nécessaire pour les étapes ultérieures de cette procédure.  
  
    ```  
    Sub EmptySub() End Sub  
    ```  
  
7.  Enregistrez le document et quittez Word.  
  
## Création du projet  
 Vous pouvez maintenant créer un projet au niveau du document pour Word qui utilise le document prenant en charge les macros que vous avez créé précédemment.  
  
#### Pour créer un projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**. Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
3.  Dans le volet Modèles, développez **Visual Basic** puis **Office\/SharePoint**.  
  
4.  Sélectionnez le nœud **Compléments Office**.  
  
5.  Dans la liste des modèles de projet, sélectionnez le projet **Document Word 2010** ou **Document Word 2013**.  
  
6.  Dans la zone **Nom**, tapez **AppelCodeDeVBA**.  
  
7.  Cliquez sur **OK**.  
  
     L'**Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8.  Sélectionnez **Copier un document existant**, puis, dans la zone **Chemin d'accès complet du document existant**, spécifiez l'emplacement du document **DocumentAvecVBA** que vous avez créé précédemment. Si vous utilisez votre propre document prenant en charge les macros, spécifiez l'emplacement de ce document à la place.  
  
9. Cliquez sur **Terminer**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le document **DocumentAvecVBA** dans le concepteur et ajoute le projet **AppelCodeDeVBA** dans l'**Explorateur de solutions**.  
  
## Approbation de l'emplacement du document  
 Avant d'exposer le code dans votre solution au code VBA dans le document, vous devez approuver VBA dans le document à exécuter. Pour ce faire, plusieurs méthodes sont possibles. Pour cette procédure pas à pas, approuvez l'emplacement du document dans le **Centre de gestion de la confidentialité** dans Word.  
  
#### Pour approuver l'emplacement du document  
  
1.  Démarrez Word.  
  
2.  Cliquez sur l'onglet **Fichier**.  
  
3.  Cliquez sur le bouton **Options Word**.  
  
4.  Dans le volet des catégories, cliquez sur **Centre de gestion de la confidentialité**.  
  
5.  Dans le volet d'informations, cliquez sur **Paramètres du Centre de gestion de la confidentialité**.  
  
6.  Dans le volet des catégories, cliquez sur **Emplacements approuvés**.  
  
7.  Dans le volet d'informations, cliquez sur **Ajouter un nouvel emplacement**.  
  
8.  Dans la boîte de dialogue **Emplacement approuvé de Microsoft Office**, accédez au dossier qui contient le projet **AppelCodeDeVBA**.  
  
9. Sélectionnez **Les sous\-dossiers de cet emplacement sont également approuvés**.  
  
10. Dans la boîte de dialogue **Emplacement approuvé de Microsoft Office**, cliquez sur **OK**.  
  
11. Dans la boîte de dialogue **Centre de gestion de la confidentialité**, cliquez sur **OK**.  
  
12. Dans la boîte de dialogue **Options Word**, cliquez sur **OK**.  
  
13. Quittez Word.  
  
## Ajout d'une méthode à la classe ThisDocument  
 Maintenant que le projet VBA est configuré, ajoutez une méthode à la classe d'élément hôte `ThisDocument` que vous pouvez appeler à partir du code VBA.  
  
#### Pour ajouter une méthode à la classe ThisDocument  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.vb**, puis cliquez sur **Afficher le code**.  
  
     Le fichier **ThisDocument.vb** s'ouvre dans l'éditeur de code.  
  
2.  Ajoutez la méthode suivante à la classe `ThisDocument`. Cette méthode crée une table de deux lignes et deux colonnes au début du document. Les paramètres spécifient le texte qui est affiché dans la première ligne. Plus loin dans cette procédure pas à pas, vous appellerez cette méthode à partir du code VBA figurant dans le document.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CallingVBCustomizationFromVBA/VB/ThisDocument.vb#1)]  
  
3.  Générez le projet.  
  
## Exposition de la méthode au code VBA  
 Pour exposer la méthode `CreateTable` au code VBA dans le document, définissez la propriété **EnableVbaCallers** pour l'élément hôte `ThisDocument` sur **True**.  
  
#### Pour exposer la méthode au code VBA  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier **ThisDocument.vb**.  
  
     Le fichier **DocumentAvecVBA** s'ouvre dans le concepteur.  
  
2.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **EnableVbaCallers** et remplacez sa valeur par **True**.  
  
3.  Cliquez sur **OK** dans le message qui s'affiche.  
  
4.  Générez le projet.  
  
## Appel de la méthode à partir du code VBA  
 Vous pouvez maintenant appeler la méthode `CreateTable` à partir du code VBA figurant dans le document.  
  
> [!NOTE]  
>  Dans cette procédure pas à pas, vous allez ajouter du code VBA au document lors du débogage du projet. Le code VBA que vous ajoutez à ce document sera remplacé la prochaine fois que vous générerez le projet, car Visual Studio remplace le document dans le dossier de sortie de génération par une copie du document provenant du dossier principal du projet. Si vous souhaitez enregistrer le code VBA, vous pouvez le copier dans le document, dans le dossier du projet. Pour plus d'informations, consultez [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### Pour appeler la méthode à partir du code VBA  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sous l'onglet **Développeur**, dans le groupe **Code**, cliquez sur **Visual Basic**.  
  
     Visual Basic Editor s'ouvre.  
  
3.  Dans le menu **Insérer**, cliquez sur **Module**.  
  
4.  Ajoutez le code ci\-dessous au nouveau module.  
  
     Ce code appelle la méthode `CreateTable` dans l'assembly de personnalisation. La macro accède à cette méthode en utilisant la propriété `CallVSTOAssembly` de l'objet `ThisDocument`. Cette propriété a été générée automatiquement quand vous avez défini la propriété **EnableVbaCallers** précédemment dans cette procédure pas à pas.  
  
    ```  
    Sub CreateTable() Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date") End Sub  
    ```  
  
5.  Appuyez sur F5.  
  
6.  Vérifiez qu'une nouvelle table a été ajoutée au document.  
  
7.  Quittez Word sans enregistrer vos modifications.  
  
## Étapes suivantes  
 Pour en savoir plus sur l'appel de code dans les solutions Office à partir de VBA, consultez les rubriques suivantes :  
  
-   Appeler du code dans une personnalisation Visual C\# à partir de VBA. Ce processus est différent du processus Visual Basic. Pour plus d'informations, consultez [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   Appeler du code dans un complément VSTO à partir de VBA. Pour plus d'informations, consultez [Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## Voir aussi  
 [Combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Comment : exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Comment : exposer du code à VBA dans un projet Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  