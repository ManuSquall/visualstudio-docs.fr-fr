---
title: 'Procédure pas à pas : Affichage de données sur un formulaire Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f623f639458a9f5c9c055b5d6de384f6fd39cad1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201200"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>Procédure pas à pas : affichage de données sur un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'un des scénarios les plus courants dans le développement d'application consiste à afficher des données dans un formulaire d'une application Windows. Vous pouvez afficher des données sur un formulaire en faisant glisser des éléments à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) vers le formulaire. Cette procédure pas à pas crée un formulaire simple qui affiche les données d'une seule table dans plusieurs contrôles individuels. Cet exemple utilise la table `Customers` de l'exemple de base de données Northwind.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un nouveau **Windows Application** projet.  
  
-   Création et configuration d’un dataset avec le [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Sélection du contrôle à créer sur le formulaire lorsque vous faites glisser des éléments à partir de la **des Sources de données** fenêtre. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Création d’un contrôle lié aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers votre formulaire.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind. Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Création de l'application Windows  
 La première étape consiste à créer un **Windows Application** projet.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Pour créer le projet d'application Windows  
  
1.  À partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Attribuez un nom au projet `DisplayingDataonaWindowsForm`.  
  
3.  Sélectionnez **Windows Application** et cliquez sur **OK**. Pour plus d’informations, consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Le **DisplayingDataonaWindowsForm** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="creating-the-data-source"></a>Création de la source de données  
 Cette étape crée une source de données à l’aide de la **Assistant de Configuration de Source de données** selon le `Customers` table dans la base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.  
  
4.  Sur le **choisir votre connexion de données** page, procédez comme suit :  
  
    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.  
  
         - ou -  
  
    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue...  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **suivant**.  
  
6.  Cliquez sur **suivant** sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** page.  
  
7.  Développez le **Tables** nœud sur le **choisir vos objets de base de données** page.  
  
8.  Sélectionnez le **clients** table, puis cliquez sur **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le **clients** table s’affiche dans le **des Sources de données** fenêtre.  
  
## <a name="setting-the-controls-to-be-created"></a>Définition des contrôles à créer  
 Pour cette procédure pas à pas, les données seront dans un **détails** où les données sont affichées dans des contrôles individuels. (L’autre approche est la valeur par défaut **grille** où les données sont affichées dans un <xref:System.Windows.Forms.DataGridView> contrôle.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Pour définir le type de dépôt des éléments de la fenêtre Sources de données  
  
1.  Développez le **clients** nœud dans le **des Sources de données** fenêtre.  
  
2.  Modifier le type de déplacement de la **clients** table **détails** en sélectionnant **détails** dans la liste déroulante sur le **clients** nœud. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Modifier le **CustomerID** le type de déplacement de la colonne à une étiquette en sélectionnant **étiquette** à partir de la liste de contrôle sur le **CustomerID** nœud.  
  
## <a name="creating-the-form"></a>Création du formulaire  
 Créer les contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers votre formulaire.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire  
  
-   Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre vers le formulaire.  
  
     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
## <a name="testing-the-application"></a>Test de l'application  
  
#### <a name="to-run-the-application"></a>Pour exécuter l'application  
  
-   Appuyez sur F5.  
  
-   Parcourez les enregistrements à l'aide du contrôle <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un formulaire Windows lié aux données. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout d'une fonctionnalité de recherche au formulaire. Pour plus d’informations, consultez [Comment : ajouter une requête paramétrable à une Application de formulaires Windows](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Ajoutez une fonctionnalité pour renvoyer des mises à jour à la base de données. Pour plus d’informations, consultez [procédure pas à pas : enregistrement de données à une base de données (Table unique)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Ajout de la `Orders` table au jeu de données en sélectionnant **configurer le jeu de données avec l’Assistant** depuis le **des Sources de données** fenêtre. Puis vous pouvez ajouter des contrôles qui affichent les données associées en faisant glisser le **commandes** nœud (celui ci-dessous, le **télécopie** colonne dans le **clients** table) vers le formulaire. Pour plus d’informations, consultez la page [Comment : afficher des données connexes dans une application Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)