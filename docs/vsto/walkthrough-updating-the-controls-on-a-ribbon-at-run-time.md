---
title: 'Procédure pas à pas : Mise à jour les contrôles sur un ruban lors de l’exécution'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 40072b1dcd6b24f552a3c87c8241ea4498229053
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389148"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Procédure pas à pas : Mise à jour les contrôles sur un ruban lors de l’exécution

Cette procédure pas à pas montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles sur un ruban après le chargement du ruban dans l’application Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

L’exemple tire des données de l’exemple de base de données Northwind pour remplir une zone de liste modifiable et un menu dans Microsoft Office Outlook. Éléments que vous sélectionnez dans ces contrôles automatiquement renseigner les champs comme **à** et **sujet** dans un message électronique.

Cette procédure pas à pas décrit les tâches suivantes :

-   Créer un nouveau projet de complément Outlook VSTO.

-   Créer un groupe de ruban personnalisé.

-   Ajouter le groupe personnalisé à un onglet intégré.

-   Mettre à jour les contrôles du ruban lors de l’exécution.

> [!NOTE]
> Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Créer un nouveau projet de complément Outlook VSTO

Commencez par créer un projet de complément VSTO Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Pour créer un projet de complément VSTO Outlook

1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créer un projet de complément Outlook VSTO portant le nom **Ribbon_Update_At_Runtime**.

2.  Dans la boîte de dialogue **Nouveau projet** , sélectionnez **Créer le répertoire pour la solution**.

3.  Enregistrez le projet dans le répertoire de projet par défaut.

     Pour plus d’informations, consultez [Comment : les projets Office de créer dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Conception d’un groupe de ruban personnalisé

Le ruban pour cet exemple s’affichera lorsqu’un utilisateur composera un nouveau message électronique. Pour créer un groupe personnalisé pour le ruban, tout d’abord ajouter un élément de ruban à votre projet, puis concevez le groupe dans le Concepteur de ruban. Ce groupe personnalisé vous aideront à générer des messages de courrier électronique de suivi aux clients en extrayant des noms et historiques à partir d’une base de données de commande.

### <a name="to-design-a-custom-group"></a>Pour concevoir un groupe personnalisé

1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)**.

3.  Modifier le nom du nouveau ruban par **CustomerRibbon**, puis cliquez sur **ajouter**.

     Le *CustomerRibbon.cs* ou *CustomerRibbon.vb* s’ouvre dans le Concepteur de ruban et affiche un onglet par défaut et un groupe.

4.  Cliquez sur le Concepteur de ruban pour le sélectionner.

5.  Dans le **propriétés** fenêtre, cliquez sur la flèche déroulante en regard du **RibbonType** propriété, puis cliquez sur **Microsoft.Outlook.Mail.Compose**.

     Ainsi, le ruban s’affichera lorsque l’utilisateur composera un nouveau message électronique dans Outlook.

6.  Dans le Concepteur de ruban, cliquez sur **Group1** pour le sélectionner.

7.  Dans le **propriétés** fenêtre, définissez **étiquette** à **Customer Purchases**.

8.  À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser un **ComboBox** sur le **Customer Purchases** groupe.

9. Cliquez sur **ComboBox1** pour le sélectionner.

10. Dans le **propriétés** fenêtre, définissez **étiquette** à **clients**.

11. À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser un **Menu** sur le **Customer Purchases** groupe.

12. Dans le **propriétés** fenêtre, définissez **étiquette** à **produit acheté**.

13. Définissez **dynamique** à **true**.

     Ainsi, vous pouvez ajouter et supprimer des contrôles dans le menu lors de l’exécution après le chargement du ruban dans l’application Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Ajouter le groupe personnalisé à un onglet intégré

Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’un Explorateur ou inspecteur Outlook. Au cours de cette procédure, vous allez ajouter le groupe personnalisé à un onglet intégré, puis spécifier la position de ce groupe sur l'onglet.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Pour ajouter le groupe personnalisé à un onglet intégré

1.  Cliquez sur le **TabAddins (intégré)** onglet pour le sélectionner.

2.  Dans le **propriétés** fenêtre, développez le **ControlId** propriété, puis définissez **OfficeId** à **valeur TabNewMailMessage**.

     Cette opération ajoute le **Customer Purchases** groupe la **Messages** onglet du ruban qui s’affiche dans un nouveau message électronique.

3.  Cliquez sur le **Customer Purchases** groupe pour le sélectionner.

4.  Dans le **propriétés** fenêtre, développez le **Position** propriété, cliquez sur la flèche déroulante en regard du **PositionType** propriété, puis cliquez sur  **BeforeOfficeId**.

5.  Définir le **OfficeId** propriété **GroupClipboard**.

     Cela positionne le **Customer Purchases** groupe avant du **Presse-papiers** groupe de la **Messages** onglet.

## <a name="create-the-data-source"></a>Créer la source de données

Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1.  Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

     Cette opération démarre le **Assistant de Configuration de Source de données**.

2.  Sélectionnez **base de données**, puis cliquez sur **suivant**.

3.  Sélectionnez **Dataset**, puis cliquez sur **suivant**.

4.  Sélectionnez une connexion de données à la base de données Microsoft SQL Server Compact 4.0 d’exemple Northwind ou ajoutez une nouvelle connexion à l’aide de la **nouvelle connexion** bouton.

5.  Une fois une connexion a été sélectionnée ou créée, cliquez sur **suivant**.

6.  Cliquez sur **suivant** pour enregistrer la chaîne de connexion.

7.  Sur le **choisir vos objets de base de données** page, développez **Tables**.

8.  Cochez la case située en regard de chacune des tables suivantes :

    1.  **Clients**

    2.  **Détails de la commande**

    3.  **Commandes**

    4.  **Produits**

9. Cliquez sur **Terminer**.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Mettre à jour des contrôles dans le groupe personnalisé lors de l’exécution

Utilisez le modèle objet de ruban pour effectuer les tâches suivantes :

-   Ajouter des noms de clients à la **clients** zone de liste déroulante.

-   Ajouter des contrôles menu et un bouton à la **Products Purchased** menu qui représentent les commandes et les produits vendus.

-   Remplir à, objet et corps de champs des nouveaux messages électroniques à l’aide des données à partir de la **clients** zone de liste déroulante et **Products Purchased** menu.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Pour mettre à jour des contrôles dans le groupe personnalisé en utilisant le modèle objet de ruban

1. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

2. Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **.NET** onglet, sélectionnez le **System.Data.Linq** assembly, puis cliquez sur **OK**.

    Cet assembly contient des classes pour l'utilisation de requêtes LINQ (Language-Integrated Queries). Vous utiliserez LINQ pour remplir des contrôles du groupe personnalisé avec des données de la base de données Northwind.

3. Dans **l’Explorateur de solutions**, cliquez sur **CustomerRibbon.cs** ou **CustomerRibbon.vb** pour le sélectionner.

4. Sur le **vue** menu, cliquez sur **Code**.

    Le fichier de code du ruban s'ouvre dans l'éditeur de code.

5. Ajoutez les instructions suivantes au début du fichier de code du ruban. Ces instructions facilitent l'accès aux espaces de noms LINQ et à l'espace de noms de l'assembly PIA (Primary Interop Assembly) d'Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Ajoutez le code suivant à l’intérieur de la `CustomerRibbon` classe. Ce code déclare les adaptateurs de table et de table de données que vous utiliserez pour stocker les informations des tables Customer, Orders, Order Details et Product de la base de données Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Ajoutez le bloc de code suivant à la classe `CustomerRibbon`. Ce code ajoute trois méthodes d’assistance qui créent des contrôles pour le ruban lors de l’exécution.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Remplacez la méthode de gestionnaire d'événements `CustomerRibbon_Load` par le code suivant. Ce code utilise une requête LINQ pour effectuer les tâches suivantes :

   - Remplir le **clients** zone de liste déroulante à l’aide de l’ID et le nom de 20 clients dans la base de données Northwind.

   - Appeler la méthode d'assistance `PopulateSalesOrderInfo`. Cette méthode met à jour le **ProductsPurchased** menu avec les numéros de commande qui se rapportent au client actuellement sélectionné.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Ajoutez le code suivant à la classe `CustomerRibbon` . Ce code utilise des requêtes LINQ pour effectuer les tâches suivantes :

   - Ajoute un sous-menu à la **ProductsPurchased** menu pour chaque commande client associées au client sélectionné.

   - Ajouter des boutons à chaque sous-menu pour les produits associés à la commande client.

   - Ajouter des gestionnaires d'événements à chaque bouton.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier de code du ruban.

     Le Concepteur de ruban s'ouvre.

11. Dans le Concepteur de ruban, double-cliquez sur le **clients** zone de liste déroulante.

     Le fichier de code du ruban s'ouvre dans l'éditeur de code, et le gestionnaire d'événements `ComboBox1_TextChanged` s'affiche.

12. Remplacez le gestionnaire d'événements `ComboBox1_TextChanged` par le code suivant. Ce code exécute les tâches suivantes :

    - Appeler la méthode d'assistance `PopulateSalesOrderInfo`. Cette méthode met à jour le **Products Purchased** menu avec les commandes relatives au client sélectionné.

    - Appeler la méthode d'assistance `PopulateMailItem` et passer le texte actuel, qui est le nom du client sélectionné. Cette méthode remplit à, objet et corps de champs des nouveaux messages électroniques.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Ajoutez le gestionnaire d’événements `Click` suivant à la classe `CustomerRibbon` . Ce code ajoute le nom des produits sélectionnés au champ corps des nouveaux messages électroniques.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Ajoutez le code suivant à la classe `CustomerRibbon` . Ce code exécute les tâches suivantes :

    - Remplit la ligne à de nouveaux messages électroniques à l’aide de l’adresse de messagerie du client actuellement sélectionné.

    - Ajoute du texte aux champs objet et le corps des nouveaux messages électroniques.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Tester les contrôles dans le groupe personnalisé

Lorsque vous ouvrez un nouveau formulaire de courrier électronique dans Outlook, un groupe personnalisé nommé **Customer Purchases** apparaît sur le **Messages** onglet du ruban.

Pour créer un message de courrier électronique de suivi client, sélectionnez un client, puis sélectionnez les produits achetés par le client. Les contrôles dans le **Customer Purchases** groupe sont mis à jour lors de l’exécution avec des données à partir de la base de données Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Pour tester les contrôles dans le groupe personnalisé

1.  Appuyez sur **F5** pour exécuter votre projet.

     Outlook démarre.

2.  Dans Outlook, sur le **fichier** menu, pointez sur **New**, puis cliquez sur **Message électronique**.

     Procédez aux étapes suivantes :

    -   Une nouvelle fenêtre de l'inspecteur de message électronique s'affiche.

    -   Sur le **Message** onglet du ruban, le **Customer Purchases** groupe apparaît avant le **Presse-papiers** groupe.

    -   Le **clients** zone de liste déroulante dans le groupe est mis à jour avec les noms des clients dans la base de données Northwind.

3.  Sur le **Message** onglet du ruban, dans le **Customer Purchases** de groupe, sélectionnez un client à partir de la **clients** zone de liste déroulante.

     Procédez aux étapes suivantes :

    -   Le **Products Purchased** menu est mis à jour pour afficher chaque commande pour le client sélectionné.

    -   Chaque sous-menu de commande client est mis à jour pour afficher les produits achetés dans cette commande.

    -   Adresse de messagerie du client sélectionné est ajouté à la **à** ligne du message électronique et l’objet et le corps du message électronique sont remplis avec du texte.

4.  Cliquez sur le **Products Purchases** menu, pointez sur une commande, puis cliquez sur un produit de la commande.

     Le nom du produit est ajouté au corps du message électronique.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :

-   Ajouter une interface utilisateur contextuelle à une personnalisation au niveau du document. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

-   Étendre un formulaire Microsoft Office standard ou personnalisé. Pour plus d’informations, consultez [procédure pas à pas : concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

-   Ajouter un volet de tâches personnalisé dans Outlook. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Voir aussi

- [Accéder au ruban lors de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Comment : modifier la position d’un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)
- [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Comment : afficher complément, les erreurs d’interface utilisateur](../vsto/how-to-show-add-in-user-interface-errors.md)