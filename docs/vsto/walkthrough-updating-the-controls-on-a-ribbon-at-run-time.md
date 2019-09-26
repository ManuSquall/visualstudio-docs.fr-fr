---
title: 'Procédure pas à pas : Mettre à jour les contrôles sur un ruban au moment de l’exécution'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 425918ea32c14e6ba905d6b32864a2844d2b5a90
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255338"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Procédure pas à pas : Mettre à jour les contrôles sur un ruban au moment de l’exécution

Cette procédure pas à pas montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles sur un ruban après le chargement du ruban dans l’application Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

L'exemple extrait des données de l'exemple de base de données Northwind pour remplir une zone de liste modifiable et un menu dans Microsoft Office Outlook. Les éléments que vous sélectionnez dans ces contrôles remplissent automatiquement les champs tels que **à** et **objet** dans un message électronique.

Cette procédure pas à pas décrit les tâches suivantes :

- Créez un projet de complément VSTO Outlook.

- Concevoir un groupe de ruban personnalisé.

- Ajoutez le groupe personnalisé à un onglet intégré.

- Met à jour les contrôles sur le ruban au moment de l’exécution.

> [!NOTE]
> Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Créer un projet de complément VSTO Outlook

Commencez par créer un projet de complément VSTO Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Pour créer un projet de complément VSTO Outlook

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de complément VSTO Outlook portant le nom **Ribbon_Update_At_Runtime**.

2. Dans la boîte de dialogue **Nouveau projet** , sélectionnez **Créer le répertoire pour la solution**.

3. Enregistrez le projet dans le répertoire de projet par défaut.

     Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

## <a name="design-a-custom-ribbon-group"></a>Concevoir un groupe de ruban personnalisé

Le ruban de cet exemple s’affiche lorsqu’un utilisateur compose un nouveau message électronique. Pour créer un groupe personnalisé pour le ruban, commencez par ajouter un élément de ruban à votre projet, puis concevez le groupe dans le concepteur de ruban. Ce groupe personnalisé vous aide à générer des messages électroniques de suivi pour les clients en extrayant des noms et des historiques de commande à partir d’une base de données.

### <a name="to-design-a-custom-group"></a>Pour concevoir un groupe personnalisé

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)** .

3. Remplacez le nom du nouveau ruban par **CustomerRibbon**, puis cliquez sur **Ajouter**.

     Le fichier *CustomerRibbon.cs* ou *CustomerRibbon. vb* s’ouvre dans le concepteur de ruban et affiche un onglet et un groupe par défaut.

4. Cliquez sur le Concepteur de ruban pour le sélectionner.

5. Dans la fenêtre **Propriétés** , cliquez sur la flèche déroulante en regard de la propriété **RibbonType** , puis cliquez sur **Microsoft. Outlook. mail. compose**.

     Cela permet au ruban d’apparaître lorsque l’utilisateur compose un nouveau message électronique dans Outlook.

6. Dans le concepteur de ruban, cliquez sur **Group1** pour le sélectionner.

7. Dans la fenêtre **Propriétés** , affectez à **label** la valeur **Customer Purchases**.

8. Sous l’onglet **contrôles de ruban Office** de la **boîte à outils**, faites glisser un **contrôle ComboBox** sur le groupe **Customer Purchases** .

9. Cliquez sur **ComboBox1** pour le sélectionner.

10. Dans la fenêtre **Propriétés** , affectez à **label** la valeur **Customers**.

11. À partir de l’onglet **contrôles de ruban Office** de la **boîte à outils**, faites glisser un **menu** vers le groupe **Customer Purchases** .

12. Dans la fenêtre **Propriétés** , affectez à **label** la valeur **Product purchased**.

13. Affectez à **Dynamic** la **valeur true**.

     Cela vous permet d’ajouter et de supprimer des contrôles dans le menu au moment de l’exécution après le chargement du ruban dans l’application Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Ajouter le groupe personnalisé à un onglet intégré

Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’un explorateur ou d’un inspecteur Outlook. Au cours de cette procédure, vous allez ajouter le groupe personnalisé à un onglet intégré, puis spécifier la position de ce groupe sur l'onglet.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Pour ajouter le groupe personnalisé à un onglet intégré

1. Cliquez sur l’onglet **TabAddIns (intégré)** pour le sélectionner.

2. Dans la fenêtre **Propriétés** , développez la propriété **ControlID** , puis affectez à **OfficeId** la valeur **TabNewMailMessage**.

     Cela ajoute le groupe **Customer Purchases** à l’onglet **messages** du ruban qui s’affiche dans un nouveau message électronique.

3. Cliquez sur le groupe **Customer Purchases** pour le sélectionner.

4. Dans la fenêtre **Propriétés** , développez la propriété **position** , cliquez sur la flèche déroulante à côté de la propriété **PositionType** , puis cliquez sur **BeforeOfficeId**.

5. Affectez à la propriété **OfficeId** la valeur **GroupClipboard**.

     Cela positionne le groupe **Customer Purchases** avant le groupe **Clipboard** de l’onglet **messages** .

## <a name="create-the-data-source"></a>Créer la source de données

Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

     L' **Assistant Configuration de source de données**démarre.

2. Sélectionnez **base de données**, puis cliquez sur **suivant**.

3. Sélectionnez **DataSet**, puis cliquez sur **suivant**.

4. Sélectionnez une connexion de données à l’exemple Northwind Microsoft SQL Server Compact base de données 4,0 ou ajoutez une nouvelle connexion à l’aide du bouton **nouvelle connexion** .

5. Après avoir sélectionné ou créé une connexion, cliquez sur **suivant**.

6. Cliquez sur **suivant** pour enregistrer la chaîne de connexion.

7. Dans la page **choisir vos objets de base de données** , développez **tables**.

8. Cochez la case située en regard de chacune des tables suivantes :

    1. **Acheteurs**

    2. **Détails de la commande**

    3. **O.f.**

    4. **Produits**

9. Cliquez sur **Terminer**.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Mettre à jour les contrôles dans le groupe personnalisé au moment de l’exécution

Utilisez le modèle objet de ruban pour effectuer les tâches suivantes :

- Ajoutez des noms de clients à la zone de liste modifiable **Customers** .

- Ajoutez des contrôles de menu et de bouton au menu **Products Purchased** qui représente les commandes et les produits vendus.

- Remplissez les champs à, objet et corps des nouveaux messages électroniques à l’aide des données de la zone de liste déroulante **clients** et du menu **produits achetés** .

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Pour mettre à jour des contrôles dans le groupe personnalisé en utilisant le modèle objet de ruban

1. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **.net** , sélectionnez l’assembly **System. Data. Linq** , puis cliquez sur **OK**.

    Cet assembly contient des classes pour l'utilisation de requêtes LINQ (Language-Integrated Queries). Vous utiliserez LINQ pour remplir des contrôles du groupe personnalisé avec des données de la base de données Northwind.

3. Dans **Explorateur de solutions**, cliquez sur **CustomerRibbon.cs** ou **CustomerRibbon. vb** pour le sélectionner.

4. Dans le menu **affichage** , cliquez sur **code**.

    Le fichier de code du ruban s'ouvre dans l'éditeur de code.

5. Ajoutez les instructions suivantes au début du fichier de code du ruban. Ces instructions facilitent l'accès aux espaces de noms LINQ et à l'espace de noms de l'assembly PIA (Primary Interop Assembly) d'Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Ajoutez le code suivant à l' `CustomerRibbon` intérieur de la classe. Ce code déclare les adaptateurs de table et de table de données que vous utiliserez pour stocker les informations des tables Customer, Orders, Order Details et Product de la base de données Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Ajoutez le bloc de code suivant à la classe `CustomerRibbon`. Ce code ajoute trois méthodes d’assistance qui créent des contrôles pour le ruban au moment de l’exécution.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Remplacez la méthode de gestionnaire d'événements `CustomerRibbon_Load` par le code suivant. Ce code utilise une requête LINQ pour effectuer les tâches suivantes :

   - Renseignez la zone de liste déroulante **Customers** en utilisant l’ID et le nom de 20 clients dans la base de données Northwind.

   - Appeler la méthode d'assistance `PopulateSalesOrderInfo`. Cette méthode met à jour le menu **ProductsPurchased** avec les numéros de commande qui se rapportent au client actuellement sélectionné.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Ajoutez le code suivant à la classe `CustomerRibbon` . Ce code utilise des requêtes LINQ pour effectuer les tâches suivantes :

   - Ajoute un sous-menu au menu **ProductsPurchased** pour chaque commande client associée au client sélectionné.

   - Ajouter des boutons à chaque sous-menu pour les produits associés à la commande client.

   - Ajouter des gestionnaires d'événements à chaque bouton.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. Dans **Explorateur de solutions**, double-cliquez sur le fichier de code du ruban.

     Le Concepteur de ruban s'ouvre.

11. Dans le concepteur de ruban, double-cliquez sur la zone de liste déroulante **Customers** .

     Le fichier de code du ruban s'ouvre dans l'éditeur de code, et le gestionnaire d'événements `ComboBox1_TextChanged` s'affiche.

12. Remplacez le gestionnaire d'événements `ComboBox1_TextChanged` par le code suivant. Ce code exécute les tâches suivantes :

    - Appeler la méthode d'assistance `PopulateSalesOrderInfo`. Cette méthode met à jour le menu **Products Purchased** avec les commandes client associées au client sélectionné.

    - Appeler la méthode d'assistance `PopulateMailItem` et passer le texte actuel, qui est le nom du client sélectionné. Cette méthode remplit les champs à, objet et corps des nouveaux messages électroniques.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Ajoutez le gestionnaire d’événements `Click` suivant à la classe `CustomerRibbon` . Ce code ajoute le nom des produits sélectionnés dans le champ corps des nouveaux messages électroniques.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Ajoutez le code suivant à la classe `CustomerRibbon` . Ce code exécute les tâches suivantes :

    - Remplit la ligne à des nouveaux messages électroniques à l’aide de l’adresse de messagerie du client actuellement sélectionné.

    - Ajoute du texte aux champs objet et corps des nouveaux messages électroniques.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Tester les contrôles dans le groupe personnalisé

Lorsque vous ouvrez un nouveau formulaire de courrier dans Outlook, un groupe personnalisé nommé **Customer Purchases** s’affiche sous l’onglet **messages** du ruban.

Pour créer un message électronique de suivi des clients, sélectionnez un client, puis sélectionnez les produits achetés par le client. Les contrôles du groupe **Customer Purchases** sont mis à jour au moment de l’exécution avec les données de la base de données Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Pour tester les contrôles dans le groupe personnalisé

1. Appuyez sur **F5** pour exécuter votre projet.

     Outlook démarre.

2. Dans Outlook, dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **message électronique**.

     Procédez aux étapes suivantes :

    - Une nouvelle fenêtre de l'inspecteur de message électronique s'affiche.

    - Sous l’onglet **message** du ruban, le groupe **Customer Purchases** s’affiche avant le groupe **Clipboard** .

    - La zone de liste déroulante **Customers** du groupe est mise à jour avec les noms des clients dans la base de données Northwind.

3. Sous l’onglet **message** du ruban, dans le groupe **Customer Purchases** , sélectionnez un client à partir de la zone de liste déroulante **Customers** .

     Procédez aux étapes suivantes :

    - Le menu **produits achetés** est mis à jour pour afficher chaque commande client pour le client sélectionné.

    - Chaque sous-menu de commande client est mis à jour pour afficher les produits achetés dans cette commande.

    - L’adresse de messagerie du client sélectionné est ajoutée à la ligne **à** du message électronique, et l’objet et le corps du message électronique sont remplis avec du texte.

4. Cliquez sur le menu **Products Purchases** , pointez sur une commande client, puis cliquez sur un produit de la commande client.

     Le nom du produit est ajouté au corps du message électronique.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :

- Ajouter une interface utilisateur contextuelle à une personnalisation au niveau du document. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

- Étendre un formulaire Microsoft Office standard ou personnalisé. Pour plus d’informations, consultez [Procédure pas à pas : Concevoir une zone](../vsto/walkthrough-designing-an-outlook-form-region.md)de formulaire Outlook.

- Ajouter un volet de tâches personnalisé dans Outlook. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Voir aussi

- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Guide pratique pour Prise en main de la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Vue d’ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Guide pratique pour Modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Guide pratique pour Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)
- [Guide pratique pour Ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Guide pratique pour Exporter un ruban à partir du concepteur de ruban vers le ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Guide pratique pour Afficher les erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)