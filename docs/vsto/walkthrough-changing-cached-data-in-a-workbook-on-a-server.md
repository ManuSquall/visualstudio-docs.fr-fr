---
title: "Proc&#233;dure pas &#224; pas&#160;: modification des donn&#233;es mises en cache dans un classeur sur un serveur | Microsoft Docs"
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
  - "données (développement Office dans Visual Studio), accéder au serveur"
  - "groupes de données (développement Office dans Visual Studio), accéder au serveur"
  - "documents (développement Office dans Visual Studio), accès aux données côté serveur"
  - "accès aux données côté serveur (développement Office dans Visual Studio)"
  - "classeurs (développement Office dans Visual Studio), modifier les données serveur"
ms.assetid: 69e13de3-9286-40cc-8c4b-1727caf761bf
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: modification des donn&#233;es mises en cache dans un classeur sur un serveur
  Cette procédure pas à pas montre comment modifier un groupe de données mis en cache dans un classeur Microsoft Office Excel sans démarrer Excel à l'aide de la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Définition d'un dataset qui contient des données de la base de données AdventureWorksLT.  
  
-   Création d'instances du groupe de données dans un projet de classeur Excel et un projet d'application console.  
  
-   Création d'un <xref:Microsoft.Office.Tools.Excel.ListObject> lié au groupe de données dans le classeur et remplissage du <xref:Microsoft.Office.Tools.Excel.ListObject> avec les données lorsque le classeur est ouvert.  
  
-   Ajout du groupe de données du classeur au cache de données.  
  
-   Modification d'une colonne de données dans le groupe de données mis en cache en exécutant le code dans l'application console, sans démarrer Excel.  
  
 Bien que cette procédure pas à pas suppose que vous exécutiez le code sur votre ordinateur de développement, le code présenté par ce biais peut être mis en œuvre sur un serveur sur lequel Excel n'est pas installé.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accès à une instance en cours d'exécution de Microsoft SQL Server ou Microsoft SQL Server Express à laquelle l'exemple de base de données AdventureWorksLT est attaché.  Vous pouvez télécharger la base de données AdventureWorksLT à partir du [site Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  Pour plus d'informations sur la façon d'attacher une base de données, consultez les rubriques suivantes :  
  
    -   Pour attacher une base de données en utilisant SQL Server Management Studio ou SQL Server Management Studio Express, consultez [Procédure : attacher une base de données \(SQL Server Management Studio\)](http://msdn.microsoft.com/fr-fr/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Pour attacher une base de données en utilisant la ligne de commande, consultez [Procédure : attacher un fichier de base de données à SQL Server Express](http://msdn.microsoft.com/fr-fr/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Création d'un projet de bibliothèque de classes définissant un groupe de données  
 Pour utiliser le même groupe de données dans un projet de classeur Excel et une application console, vous devez définir le groupe de données dans un assembly séparé référencé par ces deux projets.  Pour cette procédure pas à pas, définissez le groupe de données dans un projet de bibliothèque de classes.  
  
#### Pour créer le projet Bibliothèque de classes  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet des modèles, développez **Visual C\#** ou **Visual Basic**, puis cliquez sur **Fenêtres**.  
  
4.  Dans la liste des modèles de projet, sélectionnez **Bibliothèque de classes**.  
  
5.  Dans la zone **Nom**, tapez **AdventureWorksDataSet**.  
  
6.  Cliquez sur **Parcourir** pour accéder au dossier %UserProfile%\\Mes documents \(Windows XP ou version antérieure\) ou %UserProfile%\\Documents \(Windows Vista\), puis cliquez sur **Sélectionner un dossier**.  
  
7.  Dans la boîte de dialogue **Nouveau projet**, vérifiez que la case à cocher **Créer le répertoire pour la solution** n'est pas activée.  
  
8.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **AdventureWorksDataSet** à l'**Explorateur de solutions** et ouvre le fichier de code **Class1.cs** ou **Class1.vb**.  
  
9. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Class1.cs** ou **Class1.vb**, puis sélectionnez **Supprimer**.  Vous n'avez pas besoin de ce fichier pour cette procédure pas à pas.  
  
## Définition d'un groupe de données dans le projet de bibliothèque de classes  
 Définissez un dataset typé qui contient des données de la base de données AdventureWorksLT pour SQL Server 2005.  Plus tard au cours de cette procédure, vous ferez référence à ce dataset à partir d'un projet de classeur Excel et d'un projet d'application console.  
  
 Le groupe de données est un *groupe de données typé* qui représente les données de la table Product de la base de données AdventureWorksLT.  Pour plus d'informations sur les groupes de données typés, consultez [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Pour définir un groupe de données typé dans le projet de bibliothèque de classes  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le projet **AdventureWorksDataSet**.  
  
2.  Si la fenêtre **Sources de données** n'est pas visible, affichez\- la par, dans la barre de menus, choisissant **Afficher**, **Autres fenêtres**, **Sources de données**.  
  
3.  Choisissez **Ajouter une nouvelle source de données** pour démarrer **Assistant Configuration de source de données**.  
  
4.  Cliquez sur **Base de données**, puis sur **Suivant**.  
  
5.  Si vous disposez d'une connexion active à la base de données AdventureWorksLT, choisissez cette connexion, puis cliquez sur **Suivant**.  
  
     Dans le cas contraire, cliquez sur **Nouvelle connexion**, puis utilisez la boîte de dialogue **Ajouter une connexion** pour créer la nouvelle connexion.  Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
6.  Sur la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**, cliquez sur **Suivant**.  
  
7.  Sur la page **Choisir vos objets de base de données**, développez le nœud **Tables**, puis sélectionnez **Product \(SalesLT\)**.  
  
8.  Cliquez sur **Terminer**.  
  
     Le fichier AdventureWorksLTDataSet.xsd est ajouté au projet **AdventureWorksDataSet**.  Ce fichier définit les éléments suivants :  
  
    -   un groupe de données typé nommé `AdventureWorksLTDataSet`.  Ce groupe de données représente le contenu de la table Product dans la base de données AdventureWorksLT.  
  
    -   Un TableAdapter nommé `ProductTableAdapter`.  Ce TableAdapter peut être utilisé pour lire et écrire des données dans `AdventureWorksLTDataSet`.  Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Vous utiliserez ces deux objets plus loin dans cette procédure pas à pas.  
  
9. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **AdventureWorksDataSet**, puis sélectionnez **Générer**.  
  
     Vérifiez que la génération du projet s'exécute correctement.  
  
## Création d'un projet de classeur Excel  
 Créez un projet de classeur Excel pour assurer l'interface vers les données.  Plus loin dans cette procédure pas à pas, vous allez créer un objet <xref:Microsoft.Office.Tools.Excel.ListObject> qui affiche les données et vous allez ajouter une instance du groupe de données au cache de données dans le classeur.  
  
#### Pour créer le projet de classeur Excel  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la solution **AdventureWorksDataSet**, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
2.  Dans le volet de modèles, développez **Visual C\#** ou **Visual Basic**, puis développez **Office**.  
  
3.  Sous le nœud développé **Office**, sélectionnez le nœud **2010** .  
  
4.  Dans la liste des modèles de projet, sélectionnez le projet de classeur Excel.  
  
5.  Dans la zone **Nom**, tapez **AdventureWorksReport**.  Ne modifiez pas l'emplacement.  
  
6.  Cliquez sur **OK**.  
  
     L'**Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
7.  Assurez\-vous d'avoir sélectionné **Créer un nouveau document**, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le classeur **AdventureWorksReport** dans le concepteur et ajoute le projet **AdventureWorksReport** à l'**Explorateur de solutions**.  
  
## Ajout du groupe de données aux sources de données du projet de classeur Excel  
 Avant de pouvoir afficher le groupe de données dans le classeur Excel, vous devez l'ajouter aux sources de données du projet de classeur Excel.  
  
#### Pour ajouter le groupe de données aux sources de données dans le projet de classeur Excel  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur **Sheet1.cs** ou sur **Sheet1.vb** sous le projet **AdventureWorksReport**.  
  
     Le classeur s'ouvre dans le concepteur.  
  
2.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
     L'**Assistant Configuration de source de données** s'ouvre.  
  
3.  Cliquez sur **Objet**, puis sur **Suivant**.  
  
4.  Sur la page **Sélectionner l'objet que vous souhaitez lier**, cliquez sur **Ajouter une référence**.  
  
5.  Sous l'onglet **Projets**, cliquez sur **AdventureWorksDataSet** puis cliquez sur **OK**.  
  
6.  Sous l'espace de noms **AdventureWorksDataSet** de l'assembly **AdventureWorksDataSet**, cliquez sur **AdventureWorksLTDataSet**, puis sur **Terminer**.  
  
     La fenêtre **Sources de données** s'ouvre et **AdventureWorksLTDataSet** est ajouté à la liste des sources de données.  
  
## Création d'un ListObject lié à une instance du groupe de données  
 Pour afficher le groupe de données dans le classeur, créez un <xref:Microsoft.Office.Tools.Excel.ListObject> lié à une instance du groupe de données.  Pour plus d'informations sur la liaison des contrôles aux données, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Pour créer un ListObject lié à une instance du groupe de données  
  
1.  Dans la fenêtre **Sources de données**, développez le nœud **AdventureWorksLTDataSet**, sous **AdventureWorksDataSet**.  
  
2.  Sélectionnez le nœud **Product**, cliquez sur la flèche de déroulement qui s'affiche et sélectionnez **ListObject** dans la liste déroulante.  
  
     Si la flèche de déroulement ne s'affiche pas, assurez\-vous que le classeur est ouvert dans le concepteur.  
  
3.  Faites glisser la table **Product** vers la cellule A1.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `productListObject` est créé dans la feuille de calcul, à partir de la cellule A1.  Parallèlement, un objet DataSet nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `productBindingSource` sont ajoutés au projet.  <xref:Microsoft.Office.Tools.Excel.ListObject> est lié au <xref:System.Windows.Forms.BindingSource>, qui est lui\-même lié à l'objet de groupe de données.  
  
## Ajout du groupe de données au cache de données  
 Pour activer du code en dehors du projet de classeur Excel afin d'accéder au groupe de données du classeur, vous devez ajouter le groupe de données au cache de données.  Pour plus d'informations sur le cache de données, consultez [Données mises en cache dans des personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md) et [Mise en cache des données](../vsto/caching-data.md).  
  
#### Pour ajouter le groupe de données au cache de données  
  
1.  Dans le concepteur, cliquez sur **adventureWorksLTDataSet**.  
  
2.  Dans la fenêtre **Propriétés**, affectez à la propriété **Modifiers** la valeur **Public**.  
  
3.  Affectez à la propriété **CacheInDocument** la valeur **True**.  
  
## Initialisation du groupe de données dans le classeur  
 Avant de pouvoir extraire les données du groupe de données mis en cache à l'aide de l'application console, vous devez commencer par le remplir de données.  
  
#### Pour initialiser le groupe de données dans le classeur  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.cs** ou **Sheet1.vb** et sélectionnez **Afficher le code**.  
  
2.  Remplacez le gestionnaire d'événements `Sheet1_Startup` par le code suivant.  Ce code utilise une instance de la classe `ProductTableAdapter` définie dans le projet **AdventureWorksDataSet** pour remplir de données le groupe de données mis en cache, s'il est actuellement vide.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/AdventureWorksReport/Sheet1.vb#8)]  
  
## Point de contrôle  
 Générez et exécutez le projet de classeur Excel afin de garantir sa compilation et son exécution sans erreur.  Cette opération remplit également le groupe de données mis en cache et enregistre les données dans le classeur.  
  
#### Pour générer et exécuter le projet  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **AdventureWorksReport**, sélectionnez **Déboguer**, puis **Démarrer une nouvelle instance**.  
  
     Le projet est généré et le classeur s'ouvre dans Excel.  Vérifiez les points suivants :  
  
    -   Le <xref:Microsoft.Office.Tools.Excel.ListObject> se remplit de données.  
  
    -   La valeur de la première ligne du <xref:Microsoft.Office.Tools.Excel.ListObject> dans la colonne **ListPrice**est 1431.5.  À une étape ultérieure de cette procédure, vous utiliserez une application console pour modifier les valeurs de la colonne **ListPrice**.  
  
2.  Enregistrez le classeur.  Ne modifiez pas le nom du fichier ni l'emplacement du classeur.  
  
3.  Fermez Excel.  
  
## Création d'un projet d'application console  
 Créez un projet d'application console à utiliser pour modifier des données dans le groupe de données mis en cache dans le classeur.  
  
#### Pour créer le projet d'application console  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la solution **AdventureWorksDataSet**, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
2.  Dans le volet **Types de projets**, développez **Visual C\#** ou **Visual Basic**, puis cliquez sur **Windows**.  
  
3.  Dans le volet **Modèles**, sélectionnez **Application console**.  
  
4.  Dans la zone **Nom**, tapez **DataWriter**.  Ne modifiez pas l'emplacement.  
  
5.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **DataWriter** à l'**Explorateur de solutions** et ouvre le fichier de code **Program.cs** ou **Module1.vb**.  
  
## Modification de données dans le groupe de données mis en cache à l'aide de l'application console  
 Utilisez la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> de l'application console pour lire les données d'un objet `AdventureWorksLTDataSet` local, modifier ces données, puis les réenregistrer dans le groupe de données mis en cache.  
  
#### Pour modifier des données dans le groupe de données mis en cache  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataWriter**, puis sélectionnez **Ajouter une référence**.  
  
2.  Sous l'onglet de **.NET**, sélectionnez Microsoft.VisualStudio.Tools.Applications.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataWriter**, puis sélectionnez **Ajouter une référence**.  
  
5.  Sous l'onglet **Projets**, sélectionnez **AdventureWorksDataSet**, puis cliquez sur **OK**.  
  
6.  Ouvrez le fichier Program.cs ou Module1.vb dans l'éditeur de code.  
  
7.  Ajoutez l'instruction suivante **using** \(pour C\#\) ou **Imports** \(pour Visual Basic\) au début du fichier de code.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  Ajoutez le code suivant à la méthode `Main`.  Ce code déclare les objets suivants :  
  
    -   une instance du type `AdventureWorksLTDataSet` définie dans le projet **AdventureWorksDataSet** ;  
  
    -   Chemin du classeur AdventureWorksReport dans le dossier build du projet **AdventureWorksReport**  
  
    -   un objet <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> à utiliser pour accéder au cache de données du classeur.  
  
        > [!NOTE]  
        >  Le code suivant suppose que vous utilisez un classeur avec l'extension de fichier .xlsx.  Si le classeur de votre projet possède une autre extension de fichier, modifiez le chemin d'accès de la manière appropriée.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#6)]  
  
9. Ajoutez le code suivant à la méthode `Main` après le code inséré à l'étape précédente.  Ce code exécute les tâches suivantes :  
  
    -   Il utilise la propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> de la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour accéder au groupe de données mis en cache dans le classeur.  
  
    -   Il lit les données du groupe de données mis en cache dans le groupe de données local.  
  
    -   Il modifie la valeur `ListPrice` de chaque produit dans la table Product du groupe de données.  
  
    -   Il enregistre les modifications apportées au groupe de données mis en cache dans le classeur.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#7)]  
  
10. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataWriter**, pointez sur **Déboguer**, puis sélectionnez **Démarrer une nouvelle instance**.  
  
     L'application console affiche des messages pendant la lecture du groupe de données mis en cache dans le groupe de données local, modifie les prix des produits dans le groupe de données local et enregistre les nouvelles valeurs dans le groupe de données mis en cache.  Appuyez sur ENTRÉE pour fermer l'application.  
  
## Test du classeur  
 Lorsque vous ouvrez le classeur, <xref:Microsoft.Office.Tools.Excel.ListObject> affiche maintenant les modifications que vous avez apportées à la colonne `ListPrice` dans le groupe de données mis en cache.  
  
#### Pour tester le classeur  
  
1.  Fermez le classeur AdventureWorksReport dans le concepteur Visual Studio, s'il est toujours ouvert.  
  
2.  Ouvrez le classeur AdventureWorksReport présent dans le dossier build du projet **AdventureWorksReport**.  Par défaut, ce dossier se trouve à l'un des emplacements suivants :  
  
    -   %UserProfile%\\Mes Documents\\AdventureWorksReport\\bin\\Debug \(pour Windows XP et antérieur\)  
  
    -   %UserProfile%\\Documents\\AdventureWorksReport\\bin\\Debug \(pour Windows Vista\)  
  
3.  Vérifiez que la valeur de la colonne **ListPrice** pour la première ligne du <xref:Microsoft.Office.Tools.Excel.ListObject> est désormais 1574,65.  
  
4.  Fermez le classeur.  
  
## Voir aussi  
 [Procédure pas à pas : insertion de données dans un classeur sur un serveur](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Connexion à des données dans des applications Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  