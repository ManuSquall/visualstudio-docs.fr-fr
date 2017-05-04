---
title: "Proc&#233;dure pas &#224; pas&#160;: mise &#224; niveau des contr&#244;les sur un ruban au moment de l&#39;ex&#233;cution | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), ruban"
  - "menus dynamiques (développement Office dans Visual Studio)"
  - "ruban (développement Office dans Visual Studio), contrôles"
  - "ruban (développement Office dans Visual Studio), menu dynamique"
  - "ruban (développement Office dans Visual Studio), mettre à jour"
  - "mettre à jour des contrôles du ruban"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Proc&#233;dure pas &#224; pas&#160;: mise &#224; niveau des contr&#244;les sur un ruban au moment de l&#39;ex&#233;cution
  Cette procédure pas à pas montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles se trouvant sur un ruban après le chargement du ruban dans l'application Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 L'exemple extrait des données de l'exemple de base de données Northwind pour remplir une zone de liste modifiable et un menu dans Microsoft Office Outlook.  Les éléments que vous sélectionnez dans ces contrôles remplissent automatiquement des champs tels que **À** et **Objet** dans un message électronique.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de complément VSTO Outlook.  
  
-   Conception d'un groupe Ruban personnalisé.  
  
-   Ajout du groupe personnalisé à un onglet intégré.  
  
-   Mise à jour des contrôles sur le ruban au moment de l'exécution.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Création d'un projet de complément VSTO Outlook  
 Commencez par créer un projet de complément VSTO Outlook.  
  
#### Pour créer un projet de complément VSTO Outlook  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de complément VSTO Outlook nommé Ribbon\_Update\_At\_Runtime.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Créer le répertoire pour la solution**.  
  
3.  Enregistrez le projet dans le répertoire de projet par défaut.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Conception d'un groupe Ruban personnalisé  
 Le ruban de cet exemple s'affichera lorsqu'un utilisateur composera un nouveau message électronique.  Pour créer un groupe personnalisé pour le ruban, commencez par ajouter un élément Ruban à votre projet, puis concevez le groupe dans le Concepteur de ruban.  Ce groupe personnalisé vous permettra d'extraire d'une base de données des noms et des historiques de commande pour créer des messages électroniques de suivi pour les clients.  
  
#### Pour concevoir un groupe personnalisé  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Ruban \(Concepteur visuel\)**.  
  
3.  Remplacez le nom du nouveau ruban par **CustomerRibbon**, puis cliquez sur **Ajouter**.  
  
     Le fichier **CustomerRibbon.cs** ou **CustomerRibbon.vb** s'ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.  
  
4.  Cliquez sur le Concepteur de ruban pour le sélectionner.  
  
5.  Dans la fenêtre **Propriétés**, cliquez sur la flèche déroulante vers le bas située en regard de la propriété **RibbonType**, puis cliquez sur **Microsoft.Outlook.Mail.Compose**.  
  
     Ainsi, le ruban s'affichera lorsque l'utilisateur composera un nouveau message électronique dans Outlook.  
  
6.  Dans le Concepteur de ruban, cliquez sur **Group1** pour le sélectionner.  
  
7.  Dans la fenêtre **Propriétés**, affectez à **Label** la valeur Customer Purchases.  
  
8.  Sous l'onglet **Contrôles de ruban Office** de la **boîte à outils**, faites glisser une **zone de liste modifiable** sur le groupe **Customer Purchases**.  
  
9. Cliquez sur **ComboBox1** pour le sélectionner.  
  
10. Dans la fenêtre **Propriétés**, affectez à **Label** la valeur Customers.  
  
11. Sous l'onglet **Contrôles de ruban Office** de la **boîte à outils**, faites glisser un **menu** sur le groupe **Customer Purchases**.  
  
12. Dans la fenêtre **Propriétés**, affectez à **Label** la valeur Product Purchased.  
  
13. Affectez à **Dynamic** la valeur **true**.  
  
     Vous pouvez maintenant ajouter et supprimer des contrôles dans le menu au moment de l'exécution, après le chargement du ruban dans l'application Office.  
  
## Ajout du groupe personnalisé à un onglet intégré  
 Un onglet intégré est un onglet qui se trouve déjà sur le ruban d'un explorateur ou inspecteur Outlook.  Au cours de cette procédure, vous allez ajouter le groupe personnalisé à un onglet intégré, puis spécifier la position de ce groupe sur l'onglet.  
  
#### Pour ajouter le groupe personnalisé à un onglet intégré  
  
1.  Cliquez sur l'onglet **TabAddins \(Built\-In\)** pour le sélectionner.  
  
2.  Dans la fenêtre **Propriétés**, développez la propriété **ControlId**, puis affectez à **OfficeId** la valeur TabNewMailMessage.  
  
     Le groupe **Customer Purchases** est alors ajouté à l'onglet **Messages** du ruban qui s'affiche dans un nouveau message électronique.  
  
3.  Cliquez sur le groupe **Customer Purchases** pour le sélectionner.  
  
4.  Dans la fenêtre **Propriétés**, développez la propriété **Position**, cliquez sur la flèche déroulante vers le bas située en regard de la propriété **PositionType**, puis cliquez sur **BeforeOfficeId**.  
  
5.  Affectez à la propriété **OfficeId** la valeur GroupClipboard.  
  
     Le groupe **Customer Purchases** est alors placé avant le groupe **Presse\-papiers** de l'onglet **Messages**.  
  
## Création de la source de données  
 Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.  
  
#### Pour créer la source de données  
  
1.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
     Cette action démarre l'**Assistant Configuration de source de données**.  
  
2.  Sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
3.  Sélectionnez **Dataset**, puis cliquez sur **Suivant**.  
  
4.  Sélectionnez une connexion de données à l'exemple de base de données Microsoft SQL Server Compact 4.0 Northwind ou ajoutez une nouvelle connexion à l'aide du bouton **Nouvelle connexion**.  
  
5.  Après avoir sélectionné ou créé une connexion, cliquez sur **Suivant**.  
  
6.  Cliquez sur **Suivant** pour enregistrer la chaîne de connexion.  
  
7.  Dans la page **Choisir vos objets de base de données**, développez **Tables**.  
  
8.  Cochez la case située en regard de chacune des tables suivantes :  
  
    1.  **Customers**  
  
    2.  **Order Details**  
  
    3.  **Orders**  
  
    4.  **Products**  
  
9. Cliquez sur **Terminer**.  
  
## Mise à jour de contrôles dans le groupe personnalisé au moment de l'exécution  
 Utilisez le modèle objet de ruban pour effectuer les tâches suivantes :  
  
-   Ajouter des noms de clients à la zone de liste modifiable **Customers**.  
  
-   Ajouter des contrôles de menu et de bouton au menu **Products Purchased** qui représente les commandes et les produits vendus.  
  
-   Remplir les champs To, Subject et Body de nouveaux messages électroniques avec des données de la zone de liste modifiable **Customers** et du menu **Products Purchased**.  
  
#### Pour mettre à jour des contrôles dans le groupe personnalisé en utilisant le modèle objet de ruban  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l'onglet **.NET**, sélectionnez l'assembly **System.Data.Linq**, puis cliquez sur **OK**.  
  
     Cet assembly contient des classes pour l'utilisation de requêtes LINQ \(Language\-Integrated Queries\).  Vous utiliserez LINQ pour remplir des contrôles du groupe personnalisé avec des données de la base de données Northwind.  
  
3.  Dans l'**Explorateur de solutions**, cliquez sur **CustomerRibbon.cs** ou **CustomerRibbon.vb** pour le sélectionner.  
  
4.  Dans le menu **Affichage**, cliquez sur **Code**.  
  
     Le fichier de code du ruban s'ouvre dans l'éditeur de code.  
  
5.  Ajoutez les instructions suivantes au début du fichier de code du ruban.  Ces instructions facilitent l'accès aux espaces de noms LINQ et à l'espace de noms de l'assembly PIA \(Primary Interop Assembly\) d'Outlook.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  Ajoutez le code suivant dans la classe CustomerRibbon.  Ce code déclare les adaptateurs de table et de table de données que vous utiliserez pour stocker les informations des tables Customer, Orders, Order Details et Product de la base de données Northwind.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  Ajoutez le bloc de code suivant à la classe `CustomerRibbon`.  Ce code ajoute trois méthodes d'assistance qui créent des contrôles pour le ruban au moment de l'exécution.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  Remplacez la méthode de gestionnaire d'événements `CustomerRibbon_Load` par le code suivant.  Ce code utilise une requête LINQ pour effectuer les tâches suivantes :  
  
    -   Remplir la zone de liste modifiable **Customers** en utilisant l'ID et le nom de 20 clients de la base de données Northwind.  
  
    -   Appeler la méthode d'assistance `PopulateSalesOrderInfo`.  Cette méthode met à jour le menu **Products Purchased** avec les numéros de commande relatifs au client sélectionné.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. Ajoutez le code suivant à la classe `CustomerRibbon`.  Ce code utilise des requêtes LINQ pour effectuer les tâches suivantes :  
  
    -   Ajouter un sous\-menu au menu **Products Purchased** pour chaque commande client associée au client sélectionné.  
  
    -   Ajouter des boutons à chaque sous\-menu pour les produits associés à la commande client.  
  
    -   Ajouter des gestionnaires d'événements à chaque bouton.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier de code du ruban.  
  
     Le Concepteur de ruban s'ouvre.  
  
11. Dans le Concepteur de ruban, double\-cliquez sur la zone de liste modifiable **Customers**.  
  
     Le fichier de code du ruban s'ouvre dans l'éditeur de code, et le gestionnaire d'événements `ComboBox1_TextChanged` s'affiche.  
  
12. Remplacez le gestionnaire d'événements `ComboBox1_TextChanged` par le code suivant.  Ce code exécute les tâches suivantes :  
  
    -   Appeler la méthode d'assistance `PopulateSalesOrderInfo`.  Cette méthode met à jour le menu **Products Purchased** avec les commandes client associées au client sélectionné.  
  
    -   Appeler la méthode d'assistance `PopulateMailItem` et passer le texte actuel, qui est le nom du client sélectionné.   Cette méthode renseigne les champs To, Subject et Body des nouveaux messages électroniques.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. Ajoutez le gestionnaire d'événements Click suivant à la classe `CustomerRibbon`.  Ce code ajoute le nom des produits sélectionnés au champ Body des nouveaux messages électroniques.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. Ajoutez le code suivant à la classe `CustomerRibbon`.  Ce code exécute les tâches suivantes :  
  
    -   Renseigner la ligne To des nouveaux messages électroniques avec l'adresse électronique du client actuellement sélectionné.  
  
    -   Ajouter du texte aux champs Subject et Body des nouveaux messages électroniques.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## Test des contrôles dans le groupe personnalisé  
 Lorsque vous ouvrez un nouveau formulaire de courrier électronique dans Outlook, un groupe personnalisé nommé **Customer Purchases** s'affiche sous l'onglet **Messages** du ruban.  
  
 Pour créer un message électronique de suivi des clients, sélectionnez un client, puis les produits achetés par ce client.  Les contrôles du groupe **Customer Purchases** sont mis à jour au moment de l'exécution avec les données de la base de données Northwind.  
  
#### Pour tester les contrôles dans le groupe personnalisé  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
     Outlook démarre.  
  
2.  Dans le menu**Fichier** d'Outlook, pointez sur **Nouveau**, puis cliquez sur **Message**.  
  
     Les actions suivantes se produisent :  
  
    -   Une nouvelle fenêtre de l'inspecteur de message électronique s'affiche.  
  
    -   Sous l'onglet **Message** du ruban, le groupe **Customer Purchases** apparaît avant le groupe **Presse\-papiers**.  
  
    -   La zone de liste modifiable **Customers** du groupe est mise à jour avec les noms de clients de la base de données Northwind.  
  
3.  Sous l'onglet **Message** du ruban, dans le groupe **Customer Purchases**, sélectionnez un client dans la zone de liste modifiable **Customers**.  
  
     Les actions suivantes se produisent :  
  
    -   Le menu **Products Purchased** est mis à jour pour afficher chaque commande du client sélectionné.  
  
    -   Chaque sous\-menu de commande client est mis à jour pour afficher les produits achetés dans cette commande.  
  
    -   L'adresse électronique du client sélectionné est ajoutée à la ligne **À** du message électronique, et l'objet et le corps du message sont remplis avec du texte.  
  
4.  Cliquez sur le menu **Products Purchases**, pointez sur une commande, puis cliquez sur un produit de la commande.  
  
     Le nom du produit est ajouté au corps du message électronique.  
  
## Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :  
  
-   Ajouter une interface utilisateur contextuelle à une personnalisation au niveau du document.  Pour plus d'informations, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
-   Étendre un formulaire Microsoft Office standard ou personnalisé.  Pour plus d'informations, consultez [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Ajouter un volet de tâches personnalisé dans Outlook.  Pour plus d'informations, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
## Voir aussi  
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [LINQ \(Language Integrated Query\)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)   
 [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : modifier la position d'un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : afficher les erreurs de l'interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  