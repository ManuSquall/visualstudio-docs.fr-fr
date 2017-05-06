---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un composant WebPart pour SharePoint"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WebParts (développement SharePoint dans Visual Studio), créer"
  - "WebParts (développement SharePoint dans Visual Studio), concevoir"
  - "WebParts (développement SharePoint dans Visual Studio), développer"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un composant WebPart pour SharePoint
  Les composants WebPart permettent aux utilisateurs de modifier directement le contenu, l'apparence et le comportement des pages d'un site SharePoint à l'aide d'un navigateur.  Cette procédure pas à pas vous indique comment créer un composant WebPart à l'aide d'un modèle d'élément **WebPart** dans Visual Studio 2010.  
  
 Le composant WebPart affiche des employés dans une grille de données.  L'utilisateur spécifie l'emplacement du fichier qui contient les données sur les employés.  Il peut également filtrer la grille de données de manière à n'afficher dans la liste que les employés qui sont directeurs.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un composant WebPart à l'aide du modèle d'élément **WebPart** de Visual Studio  
  
-   Création d'une propriété pouvant être définie par l'utilisateur du composant WebPart.  Cette propriété spécifie l'emplacement du fichier de données sur les employés.  
  
-   Restitution du contenu dans un composant WebPart en ajoutant des contrôles à la collection de contrôles WebPart  
  
-   Création d'un élément de menu, désigné par « *verbe* », figurant dans le menu d'actions verbales du composant WebPart restitué.  Les verbes permettent à l'utilisateur de modifier les données qui s'affichent dans le composant WebPart.  
  
-   Test du composant WebPart dans SharePoint  
  
    > [!NOTE]  
    >  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de Microsoft Windows et SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] ou une édition de Visual Studio Application Lifecycle Management \(ALM\).  
  
## Création d'un projet SharePoint vide  
 Commencez par créer un projet SharePoint vide.  Vous ajouterez ensuite un composant WebPart au projet à l'aide du modèle d'élément **WebPart**.  
  
#### Pour créer un projet SharePoint vide  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sélectionnant l'option **Exécuter en tant qu'administrateur**.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, développez le nœud **SharePoint** sous le langage que vous souhaitez utiliser, puis sélectionnez le nœud **2010**.  
  
4.  Dans le volet **Modèles**, sélectionnez l'élément **Projet SharePoint 2010**, puis choisissez le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  Cet Assistant vous permet de sélectionner le site à utiliser pour déboguer le projet et le niveau de confiance de la solution.  
  
5.  Sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis choisissez le bouton **Terminer** pour accepter le site SharePoint local par défaut.  
  
## Ajout d'un composant WebPart au projet  
 Vous pouvez ajouter un élément **WebPart** au projet.  L'élément **WebPart** ajoute le fichier de code du composant WebPart.  Vous ajouterez ensuite du code à ce fichier pour restituer le contenu du composant WebPart.  
  
#### Pour ajouter un composant WebPart au projet  
  
1.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, dans le volet **Modèles installés**, développez le nœud **SharePoint**, puis cliquez sur **2010**.  
  
3.  Dans la liste des modèles, sélectionnez le modèle **SharePoint 2013 \- Composant Visual Web Part**, puis choisissez le bouton **OK**.  
  
     L'élément **WebPart** s'affiche dans l'**Explorateur de solutions**.  
  
## Restitution du contenu du composant WebPart  
 Vous pouvez spécifier les contrôles à afficher dans le composant WebPart en les ajoutant à la collection de contrôles de la classe WebPart.  
  
#### Pour restituer le contenu du composant WebPart  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur WebPart1.vb \(en Visual Basic\) ou WebPart1.cs \(en C\#\).  
  
     Le fichier de code du composant WebPart s'ouvre dans l'éditeur de code.  
  
2.  Ajoutez les instructions suivantes au début du fichier de code du composant WebPart.  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  Ajoutez le code suivant à la classe `WebPart1`.  Ce code déclare les champs suivants :  
  
    -   Grille de données pour afficher les employés dans le composant WebPart  
  
    -   Texte qui s'affiche sur le contrôle utilisé pour filtrer la grille de données  
  
    -   Étiquette qui affiche une erreur lorsque la grille de données ne peut pas afficher de données  
  
    -   Chaîne qui contient le chemin d'accès du fichier de données sur les employés  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  Ajoutez le code suivant à la classe `WebPart1`.  Ce code ajoute une propriété personnalisée nommée `DataFilePath` au composant WebPart.  Une propriété personnalisée est une propriété qui peut être définie par l'utilisateur dans SharePoint.  Cette propriété obtient et définit l'emplacement d'un fichier de données XML utilisé pour remplir la grille de données.  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  Remplacez la méthode `CreateChildControls` par le code ci\-dessous.  Ce code exécute les tâches suivantes :  
  
    -   Il ajoute la grille de données et l'étiquette que vous avez déclarées au cours de l'étape précédente.  
  
    -   Il lie la grille de données à un fichier XML qui contient des données sur les employés.  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  Ajoutez la méthode suivante à la classe `WebPart1`.  Ce code exécute les tâches suivantes :  
  
    -   Il crée un verbe qui s'affiche dans le menu d'actions verbales WebPart du composant WebPart restitué.  
  
    -   Il gère l'événement qui est déclenché lorsque l'utilisateur clique sur le verbe dans le menu d'actions verbales.  Ce code filtre la liste des employés qui s'affiche dans la grille de données.  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## Test du composant WebPart  
 Lorsque vous exécutez le projet, le site SharePoint s'ouvre.  Le composant WebPart est automatiquement ajouté à la galerie de composants WebPart dans SharePoint.  Vous pouvez ajouter le composant WebPart à toute page WebPart.  
  
#### Pour tester le composant WebPart  
  
1.  Collez le code XML suivant dans un fichier Bloc\-notes.  Ce fichier XML contient des exemples de données qui s'afficheront dans le composant WebPart.  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
       <employee>  
           <name>David Hamilton</name>  
           <hireDate>2001-05-11</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Karina Leal</name>  
           <hireDate>1999-04-01</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Nancy Davolio</name>  
           <hireDate>1992-05-01</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Steven Buchanan</name>  
           <hireDate>1955-03-04</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Suyama Michael</name>  
           <hireDate>1963-07-02</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
    </employees>  
    ```  
  
2.  Dans la barre de menus du Bloc\-notes, choisissez **Fichier**, **Enregistrer**.  
  
3.  Dans la boîte de dialogue **Enregistrer sous**, dans la liste déroulante **Type**, sélectionnez **Tous les fichiers**.  
  
4.  Dans la zone **Nom de fichier**, tapez data.xml.  
  
5.  Sélectionnez un dossier à l'aide du bouton **Parcourir les dossiers**, puis cliquez sur **Enregistrer**.  
  
6.  Dans Visual Studio, appuyez sur la touche **F5**.  
  
     Le site SharePoint s'ouvre.  
  
7.  Dans le menu **Actions du site**, cliquez sur **Autres options**.  
  
8.  Dans la page **Créer**, sélectionnez le type **Page de composant WebPart**, puis choisissez le bouton **Créer**.  
  
9. Dans la page **Nouvelle page de composants WebPart**, nommez la page **SampleWebPartPage.aspx**, puis choisissez le bouton **Créer**.  
  
     La page de composants WebPart s'affiche.  
  
10. Sélectionnez une zone sur la page de composants WebPart.  
  
11. En haut de la page, cliquez sur l'onglet **Insérer**, puis sur **WebPart**.  
  
12. Dans le volet **Catégories**, cliquez sur le dossier **Personnalisé**, puis sur le composant WebPart **WebPart1** et sur **Ajouter**.  
  
     Le composant WebPart s'affiche dans la page.  
  
## Test de la propriété personnalisée  
 Pour remplir la grille de données qui s'affiche dans le composant WebPart, spécifiez le chemin d'accès du fichier XML qui contient des données sur chaque employé.  
  
#### Pour tester la propriété personnalisée  
  
1.  Cliquez sur la flèche qui apparaît à droite du composant WebPart, puis choisissez **Modifier le composant WebPart** dans le menu qui s'affiche.  
  
     Un volet qui contient les propriétés du composant WebPart s'affiche à droite de la page.  
  
2.  Dans ce volet, développez le nœud **Divers**, tapez le chemin d'accès du fichier XML que vous avez précédemment créé, puis cliquez sur**Appliquer** et sur **OK**.  
  
     Vérifiez qu'une liste d'employés s'affiche dans le composant WebPart.  
  
## Test du verbe WebPart  
 Vous pouvez afficher et masquer les employés qui ne sont pas directeurs en cliquant sur un élément qui figure dans le menu d'actions verbales WebPart.  
  
#### Pour tester le verbe WebPart  
  
1.  Cliquez sur la flèche qui apparaît à droite du composant WebPart, puis choisissez **Modifier le composant WebPart** dans le menu qui s'affiche.  
  
     Seuls les employés qui sont directeurs s'affichent dans le composant WebPart.  
  
2.  Choisissez la flèche, puis choisissez **Afficher tous les employés** dans le menu qui apparaît.  
  
     Tous les employés s'affichent dans le composant WebPart.  
  
## Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procédure pas à pas : création d'un composant WebPart pour SharePoint à l'aide d'un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  