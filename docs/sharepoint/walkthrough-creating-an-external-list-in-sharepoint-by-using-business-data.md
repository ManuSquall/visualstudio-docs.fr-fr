---
title: "Procédure pas à pas : Création d’une liste externe dans SharePoint à l’aide des données d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c0954665e8b088f969d59bdad0a2ef1207c95c8f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>Procédure pas à pas : création d'une liste externe dans SharePoint à l'aide de données métiers
  Le service de connectivité de données métiers (BDC) permet à SharePoint afficher les données d’entreprise à partir d’applications de serveur principal, les services Web et les bases de données.  
  
 Cette procédure pas à pas vous montre comment créer un modèle pour le service BDC qui retourne des informations sur les contacts dans une base de données exemple. Vous allez ensuite créer une liste externe dans SharePoint à l’aide de ce modèle.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un projet.  
  
-   Ajout d’une entité au modèle.  
  
-   Ajout d’une méthode de recherche.  
  
-   Ajout d’une méthode de recherche spécifique.  
  
-   Test du projet.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)], ou [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Accès à la base de données AdventureWorks. Pour plus d’informations sur l’installation de la base de données AdventureWorks, consultez [SQL Server Sample Databases](http://go.microsoft.com/fwlink/?LinkID=117483).  
  
## <a name="creating-a-project-that-contains-a-bdc-model"></a>Création d'un projet qui contient un modèle BDC  
  
#### <a name="to-create-a-project-that-contains-a-bdc-model"></a>Pour créer un projet contenant un modèle BDC  
  
1.  Dans la barre de menus dans Visual Studio, choisissez **fichier**, **nouveau**, **projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** élément.  
  
3.  Dans le **modèles** volet, choisissez **projet SharePoint 2010**, nommez le projet **AdventureWorksTest**, puis choisissez le **OK** bouton .  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche. Dans cet Assistant, vous pouvez spécifier le site que vous allez utiliser pour déboguer le projet et définir le niveau de confiance de la solution.  
  
4.  Choisissez le **déployer une solution de batterie de serveurs** case d’option pour définir le niveau de confiance.  
  
5.  Choisissez le **Terminer** bouton pour accepter le site SharePoint local par défaut.  
  
6.  Dans **l’Explorateur de solutions**, choisissez le nœud de projet SharePoint.  
  
7.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.  
  
8.  Dans le **modèles** volet, choisissez **modèle de connectivité de données métiers (Solution de batterie uniquement)**, nommez le projet **AdventureWorksContacts**, puis choisissez le **Ajouter** bouton.  
  
## <a name="adding-data-access-classes-to-the-project"></a>Classes d’accès aux données ajout au projet  
  
#### <a name="to-add-data-access-classes-to-the-project"></a>Pour ajouter des classes d’accès aux données au projet  
  
1.  Dans la barre de menus, choisissez **outils**, **se connecter à la base de données**.  
  
     Le **ajouter une connexion** boîte de dialogue s’ouvre.  
  
2.  Ajouter une connexion à la base de données SQL Server AdventureWorks.  
  
     Pour plus d’informations, consultez [Ajouter/modifier une connexion (Microsoft SQL Server)](http://msdn.microsoft.com/en-us/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet.  
  
4.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
5.  Dans le **modèles installés** volet, choisissez la **données** nœud.  
  
6.  Dans le **modèles** volet, choisissez **Classes LINQ to SQL**.  
  
7.  Dans le **nom** , spécifiez **AdventureWorks**, puis choisissez le **ajouter** bouton.  
  
     Un fichier .dbml est ajouté au projet et le Concepteur Objet/Relationnel (Concepteur O/R) s'ouvre.  
  
8.  Dans la barre de menus, choisissez **vue**, **l’Explorateur de serveurs**.  
  
9. Dans **l’Explorateur de serveurs**, développez le nœud qui représente la base de données AdventureWorks, puis développez le **Tables** nœud.  
  
10. Ajouter le **Contact (personne)** table sur le Concepteur O/R.  
  
     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d’entité a des propriétés qui correspondent aux colonnes de la table Contact (personne).  
  
## <a name="removing-the-default-entity-from-the-bdc-model"></a>Suppression de l’entité par défaut du modèle BDC  
 Le **modèle de connectivité de données métiers** project ajoute une entité par défaut nommée Entity1 au modèle. Supprimez cette entité. Une version ultérieure, vous allez ajouter une nouvelle entité. En commençant par un modèle vide permet de réduire le nombre d’étapes requises pour effectuer la procédure pas à pas.  
  
#### <a name="to-remove-the-default-entity-from-the-model"></a>Pour supprimer l’entité par défaut du modèle  
  
1.  Dans **l’Explorateur de solutions**, développez le **BdcModel1** nœud, puis ouvrez le fichier BdcModel1.bdcm.  
  
2.  Le fichier de modèle de connectivité de données métiers s’ouvre dans le concepteur BDC.  
  
3.  Dans le concepteur, ouvrez le menu contextuel de **Entity1**, puis choisissez **supprimer**.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour Entity1.vb (en Visual Basic) ou Entity1.cs (en c#), puis choisissez **supprimer**.  
  
5.  Ouvrez le menu contextuel pour Entity1Service.vb (en Visual Basic) ou Entity1Service.cs (en c#), puis choisissez **supprimer**.  
  
## <a name="adding-an-entity-to-the-model"></a>Ajout d’une entité au modèle  
 Ajouter une entité au modèle. Vous pouvez ajouter des entités à partir de Visual Studio **boîte à outils** sur le concepteur BDC.  
  
#### <a name="to-add-an-entity-to-the-model"></a>Pour ajouter une entité au modèle  
  
1.  Dans la barre de menus, choisissez **Affichage**, **Boîte à outils**.  
  
2.  Sur le **BusinessDataConnectivity** onglet de la **boîte à outils**, ajoutez une **entité** sur le concepteur BDC.  
  
     La nouvelle entité s’affiche dans le concepteur. Visual Studio ajoute un fichier nommé EntityService.vb (en Visual Basic) ou EntityService.cs (en c#) au projet.  
  
3.  Dans la barre de menus, choisissez **vue**, **propriétés**, **fenêtre**.  
  
4.  Dans le **propriétés** , configurez la **nom** valeur de propriété à **Contact**.  
  
5.  Dans le concepteur, ouvrez le menu contextuel de l’entité, choisissez **ajouter**, puis choisissez **identificateur**.  
  
     Un nouvel identificateur s’affiche sur l’entité.  
  
6.  Dans le **propriétés** fenêtre, modifiez le nom de l’identificateur à **ContactID**.  
  
7.  Dans le **nom de Type** , choisissez **System.Int32**.  
  
## <a name="adding-a-specific-finder-method"></a>Ajout d’une méthode de recherche spécifique  
 Pour activer le service BDC afficher un contact spécifique, vous devez ajouter une méthode de recherche spécifique. Le service BDC appelle la méthode de recherche spécifique lorsqu’un utilisateur choisit un élément dans une liste et choisit ensuite le **l’élément d’affichage** bouton sur le ruban.  
  
 Ajouter une méthode de recherche spécifique à l’entité Contact à l’aide de la **détails de méthode BDC** fenêtre. Pour retourner une entité spécifique, ajoutez le code à la méthode.  
  
#### <a name="to-add-a-specific-finder-method"></a>Pour ajouter une méthode de recherche spécifique  
  
1.  Dans le concepteur BDC, choisissez le **Contact** entité.  
  
2.  Dans la barre de menus, choisissez **vue**, **autres fenêtres**, **détails de méthode BDC**.  
  
     La fenêtre Détails de méthode BDC s’ouvre.  
  
3.  Dans le **ajouter une méthode** , choisissez **créer une méthode de recherche spécifique**.  
  
     Visual Studio ajoute les éléments suivants au modèle. Ces éléments apparaissent dans le **détails de méthode BDC** fenêtre.  
  
    -   Une méthode nommée ReadItem.  
  
    -   Un paramètre d’entrée pour la méthode.  
  
    -   Un paramètre de retour de la méthode.  
  
    -   Un descripteur de type pour chaque paramètre.  
  
    -   Une instance de méthode pour la méthode.  
  
4.  Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour le **Contact** descripteur de type, puis choisissez **modifier**.  
  
     Le **Explorateur BDC** s’ouvre et affiche une vue hiérarchique du modèle.  
  
5.  Dans le **propriétés** fenêtre, ouvrez la liste à côté la **TypeName** propriété, choisissez le **projet actuel** onglet, puis choisissez le **Contact**propriété.  
  
6.  Dans le **Explorateur BDC**, ouvrez le menu contextuel de la **Contact**, puis choisissez **ajouter un descripteur de Type**.  
  
     Un nouveau descripteur de type nommé **TypeDescriptor1** s’affiche dans le **Explorateur BDC**.  
  
7.  Dans le **propriétés** , configurez la **nom** valeur de propriété à **ContactID**.  
  
8.  Ouvrez la liste à côté du **TypeName** propriété, puis choisissez **Int32**.  
  
9. Ouvrez la liste à côté du **identificateur** propriété, puis choisissez **ContactID**.  
  
10. Répétez l’étape 6 pour créer un descripteur de type pour chacun des champs suivants.  
  
    |Name|Nom de type|  
    |----------|---------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Téléphone|System.String|  
    |emailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. Dans le concepteur BDC, sur le **Contact** entité, ouvre le **ReadItem** (méthode).  
  
     Le fichier de code de service Contact s’ouvre dans l’éditeur de Code.  
  
12. Dans le `ContactService` de classe, remplacez le `ReadItem` méthode avec le code suivant. Ce code exécute les tâches suivantes :  
  
    -   Récupère un enregistrement à partir de la table Contact de la base de données AdventureWorks.  
  
    -   Retourne une entité Contact au service BDC.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="adding-a-finder-method"></a>Ajout d’une méthode de recherche  
 Pour activer le service BDC afficher les contacts dans une liste, vous devez ajouter une méthode de recherche. Ajouter une méthode de recherche à l’entité Contact à l’aide de la **détails de méthode BDC** fenêtre. Pour retourner une collection d’entités au service BDC, ajoutez le code à la méthode.  
  
#### <a name="to-add-a-finder-method"></a>Pour ajouter une méthode de recherche  
  
1.  Dans le concepteur BDC, choisissez le **Contact** entité.  
  
2.  Dans le **détails de méthode BDC** fenêtre, réduire la **ReadItem** nœud.  
  
3.  Dans le **ajouter une méthode** liste sous le **ReadList** méthode, choisissez **créer une méthode de recherche**.  
  
     Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.  
  
4.  Dans le concepteur BDC, sur le **Contact** entité, ouvre le **ReadList** (méthode).  
  
     Le fichier de code pour le service Contact s'ouvre dans l'éditeur de code.  
  
5.  Dans le `ContactService` de classe, remplacez le `ReadList` méthode avec le code suivant. Ce code exécute les tâches suivantes :  
  
    -   Récupère les données à partir de la table Contacts de la base de données AdventureWorks.  
  
    -   Retourne une liste d’entités Contact au service BDC.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="testing-the-project"></a>Test du projet  
 Lorsque vous exécutez le projet, le site SharePoint s’ouvre et Visual Studio ajoute votre modèle au service de connectivité de données métiers. Créer une liste externe dans SharePoint qui fait référence à l’entité Contact. Les données pour les contacts dans la base de données AdventureWorks s’affichent dans la liste.  
  
> [!NOTE]  
>  Vous devrez peut-être modifier vos paramètres de sécurité dans SharePoint avant de pouvoir déboguer votre solution.  Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### <a name="to-test-the-project"></a>Pour tester le projet  
  
1.  Choisissez la touche **F5**.  
  
     Le site SharePoint s’ouvre.  
  
2.  Sur le **Actions du Site** menu, choisissez le **plus d’Options** commande.  
  
3.  Sur le **créer** page, choisissez la **liste externe** modèle, puis choisissez le **créer** bouton.  
  
4.  Nom de la liste personnalisée **Contacts**.  
  
5.  Choisissez le bouton Parcourir à côté du **Type de contenu externe** champ.  
  
6.  Dans le **sélecteur de Type de contenu externe** boîte de dialogue, choisissez le **AdventureWorksContacts.BdcModel1.Contact** d’élément, puis choisissez le **créer** bouton.  
  
     SharePoint crée une liste externe qui contient des contacts de l'exemple de base de données AdventureWorks.  
  
7.  Pour tester la méthode de recherche spécifique, choisissez un contact dans la liste.  
  
8.  Dans le ruban, cliquez sur le **éléments** onglet, puis choisissez le **l’élément d’affichage** commande.  
  
     Les détails du contact que vous avez choisi s'affichent sur un formulaire.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur la conception de modèles pour le service de catalogue de données métiers dans SharePoint à partir de ces rubriques :  
  
-   [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  