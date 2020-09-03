---
title: Créer une liste externe dans SharePoint à l’aide de données d’entreprise
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29f6c4e170bce8ae7bacfc7178ebd9386f2d4416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015829"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Procédure pas à pas : création d’une liste externe dans SharePoint à l’aide de données d’entreprise

Le service de connectivité de données métiers (BDC) permet à SharePoint d’afficher des données d’entreprise à partir d’applications serveur principales, de services Web et de bases de données.

Cette procédure pas à pas vous montre comment créer un modèle pour le service BDC qui retourne des informations sur les contacts dans un exemple de base de données. Vous allez ensuite créer une liste externe dans SharePoint à l’aide de ce modèle.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet.
- Ajout d’une entité au modèle.
- Ajout d’une méthode de recherche.
- Ajout d’une méthode de recherche spécifique.
- Test du projet.

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Windows et SharePoint.

- Accès à l’exemple de base de données AdventureWorks. Pour plus d’informations sur l’installation de la base de données AdventureWorks, consultez [SQL Server exemples de bases de données](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Créer un projet qui contient un modèle BDC

1. Dans la barre de menus de Visual Studio, choisissez **fichier**  >  **nouveau**  >  **projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

2. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez l’élément **2010** .

3. Dans le volet **modèles** , choisissez **projet SharePoint 2010**, nommez le projet **AdventureWorksTest**, puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche. Dans cet Assistant, vous pouvez spécifier le site que vous utiliserez pour déboguer le projet et définir le niveau de confiance de la solution.

4. Sélectionnez la case d’option **déployer en tant que solution de batterie** pour définir le niveau de confiance.

5. Choisissez le bouton **Terminer** pour accepter le site SharePoint local par défaut.

6. Dans **Explorateur de solutions**, choisissez le nœud de projet SharePoint.

7. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

8. Dans le volet **modèles** , choisissez **modèle de connectivité de données métiers (solution de batterie uniquement)**, nommez le projet **AdventureWorksContacts**, puis cliquez sur le bouton **Ajouter** .

## <a name="add-data-access-classes-to-the-project"></a>Ajouter des classes d’accès aux données au projet

1. Dans la barre de menus, choisissez **Outils**  >  **connexion à la base de données**.

     La boîte de dialogue **Ajouter une connexion** s’ouvre.

2. Ajoutez une connexion à l’exemple de base de données SQL Server AdventureWorks.

     Pour plus d’informations, consultez [Ajouter/modifier la connexion (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

4. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

5. Dans le volet **modèles installés** , choisissez le nœud **données** .

6. Dans le volet **modèles** , choisissez **LINQ to SQL classes**.

7. Dans la zone **nom** , spécifiez **AdventureWorks**, puis cliquez sur le bouton **Ajouter** .

     Un fichier .dbml est ajouté au projet et le Concepteur Objet/Relationnel (Concepteur O/R) s'ouvre.

8. Dans la barre de menus, choisissez **Afficher**  >  **Explorateur de serveurs**.

9. Dans **Explorateur de serveurs**, développez le nœud qui représente l’exemple de base de données AdventureWorks, puis développez le nœud **tables** .

10. Ajoutez la table **contact (person)** au Concepteur O/R.

     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d’entité a des propriétés qui mappent aux colonnes dans la table contact (person).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Supprimer l’entité par défaut du modèle BDC

Le projet de **modèle de connectivité de données métiers** ajoute une entité par défaut nommée Entity1 au modèle. Supprimez cette entité. Plus tard, vous ajouterez une nouvelle entité. En commençant par un modèle vide, vous réduisez le nombre d’étapes requises pour effectuer la procédure pas à pas.

1. Dans **Explorateur de solutions**, développez le nœud **BdcModel1** , puis ouvrez le fichier *BdcModel1. BDCM* .

2. Le fichier de modèle de connectivité de données métiers s’ouvre dans le concepteur BDC.

3. Dans le concepteur, ouvrez le menu contextuel de **Entity1**, puis choisissez **supprimer**.

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel pour *Entity1. vb* (dans Visual Basic) ou *Entity1.cs* (en C#), puis choisissez **supprimer**.

5. Ouvrez le menu contextuel pour *Entity1Service. vb* (dans Visual Basic) ou *Entity1Service.cs* (en C#), puis choisissez **supprimer**.

## <a name="add-an-entity-to-the-model"></a>Ajouter une entité au modèle

Ajoutez une entité au modèle. Vous pouvez ajouter des entités à partir de la **boîte à outils** Visual Studio sur le concepteur BDC.

1. Dans la barre de menus, choisissez **Afficher**la  >  **boîte à outils**.

2. Sous l’onglet **BusinessDataConnectivity** de la **boîte à outils**, ajoutez une **entité** sur le concepteur BDC.

     La nouvelle entité s’affiche sur le concepteur. Visual Studio ajoute un fichier nommé *EntityService. vb* (dans Visual Basic) ou *EntityService.cs* (en C#) au projet.

3. Dans la barre de menus, choisissez **Afficher**la  >  **Properties**  >  **fenêtre**propriétés.

4. Dans la fenêtre **Propriétés** , affectez à la propriété **nom** la valeur **contact**.

5. Dans le concepteur, ouvrez le menu contextuel de l’entité, choisissez **Ajouter**, puis **identificateur**.

     Un nouvel identificateur apparaît sur l’entité.

6. Dans la fenêtre **Propriétés** , remplacez le nom de l’identificateur par **ContactID**.

7. Dans la liste **nom du type** , choisissez **System. Int32**.

## <a name="add-a-specific-finder-method"></a>Ajouter une méthode de recherche spécifique

Pour permettre au service BDC d’afficher un contact spécifique, vous devez ajouter une méthode de recherche spécifique. Le service BDC appelle la méthode de recherche spécifique lorsqu’un utilisateur choisit un élément dans une liste, puis choisit le bouton **afficher l’élément** sur le ruban.

Ajoutez une méthode de recherche spécifique à l’entité contact à l’aide de la fenêtre Détails de la **méthode BDC** . Pour retourner une entité spécifique, ajoutez du code à la méthode.

1. Dans le concepteur BDC, choisissez l’entité **contact** .

2. Dans la barre de menus, choisissez **Afficher**  >  **les autres**détails de la  >  **méthode BDC**Windows.

     La fenêtre Détails de la méthode BDC s’ouvre.

3. Dans la liste **Ajouter une méthode** , choisissez **créer une méthode de recherche spécifique**.

     Visual Studio ajoute les éléments suivants au modèle. Ces éléments s’affichent dans la fenêtre Détails de la **méthode BDC** .

    - Une méthode nommée ReadItem.

    - Paramètre d’entrée pour la méthode.

    - Paramètre de retour de la méthode.

    - Descripteur de type pour chaque paramètre.

    - Instance de méthode pour la méthode.

4. Dans la fenêtre **Détails de méthode BDC** , ouvrez la liste qui s’affiche pour le descripteur de type de **contact** , puis choisissez **modifier**.

     L' **Explorateur BDC** s’ouvre et fournit une vue hiérarchique du modèle.

5. Dans la fenêtre **Propriétés** , ouvrez la liste en regard de la propriété **TypeName** , choisissez l’onglet **projet actif** , puis choisissez la propriété **contact** .

6. Dans l' **Explorateur BDC**, ouvrez le menu contextuel du **contact**, puis choisissez **Ajouter un descripteur de type**.

     Un nouveau descripteur de type nommé **TypeDescriptor1** apparaît dans l' **Explorateur BDC**.

7. Dans la fenêtre **Propriétés** , définissez la valeur de la propriété **nom** sur **ContactID**.

8. Ouvrez la liste à côté de la propriété **TypeName** , puis choisissez **Int32**.

9. Ouvrez la liste en regard de la propriété **identificateur** , puis choisissez **ContactID**.

10. Répétez l’étape 6 pour créer un descripteur de type pour chacun des champs suivants.

    |Nom|Nom de type|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Téléphone|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Dans le concepteur BDC, sur l’entité **contact** , ouvrez la méthode **ReadItem** .

     Le fichier de code du service de contact s’ouvre dans l’éditeur de code.

12. Dans la `ContactService` classe, remplacez la `ReadItem` méthode par le code suivant. Ce code effectue les tâches suivantes :

    - Récupère un enregistrement de la table contact de la base de données AdventureWorks.

    - Retourne une entité de contact au service BDC.

    > [!NOTE]
    > Remplacez la valeur du `ServerName` champ par le nom de votre serveur.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Ajouter une méthode de recherche

Pour permettre au service BDC d’afficher les contacts dans une liste, vous devez ajouter une méthode de recherche. Ajoutez une méthode de recherche à l’entité contact à l’aide de la fenêtre Détails de la **méthode BDC** . Pour retourner une collection d’entités au service BDC, ajoutez du code à la méthode.

1. Dans le concepteur BDC, choisissez l’entité **contact** .

2. Dans la fenêtre **Détails de méthode BDC** , réduisez le nœud **ReadItem** .

3. Dans la liste **Ajouter une méthode** sous la méthode **ReadList (lire** , choisissez **créer une méthode de recherche**.

     Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.

4. Dans le concepteur BDC, sur l’entité **contact** , ouvrez la méthode **ReadList (lire** .

     Le fichier de code pour le service Contact s'ouvre dans l'éditeur de code.

5. Dans la `ContactService` classe, remplacez la `ReadList` méthode par le code suivant. Ce code effectue les tâches suivantes :

   - Récupère des données de la table contacts de la base de données AdventureWorks.

   - Retourne une liste d’entités de contact au service BDC.

     > [!NOTE]
     > Remplacez la valeur du `ServerName` champ par le nom de votre serveur.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Tester le projet

Lorsque vous exécutez le projet, le site SharePoint s’ouvre et Visual Studio ajoute votre modèle au service de connectivité de données métiers. Créez une liste externe dans SharePoint qui référence l’entité contact. Les données des contacts dans la base de données AdventureWorks s’affichent dans la liste.

> [!NOTE]
> Vous devrez peut-être modifier vos paramètres de sécurité dans SharePoint pour pouvoir déboguer votre solution. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Choisissez la touche **F5**.

     Le site SharePoint s’ouvre.

2. Dans le menu **actions du site** , choisissez la commande **autres options** .

3. Dans la page **créer** , choisissez le modèle **liste externe** , puis cliquez sur le bouton **créer** .

4. Nommez la liste personnalisée **contacts**.

5. Choisissez le bouton Parcourir en regard du champ **type de contenu externe** .

6. Dans la boîte de dialogue **Sélecteur de type de contenu externe** , choisissez l’élément **AdventureWorksContacts. BdcModel1. contact** , puis cliquez sur le bouton **créer** .

     SharePoint crée une liste externe qui contient des contacts de l'exemple de base de données AdventureWorks.

7. Pour tester la méthode de recherche spécifique, choisissez un contact dans la liste.

8. Dans le ruban, choisissez l’onglet **éléments** , puis choisissez la commande **afficher l’élément** .

     Les détails du contact que vous avez choisi s'affichent sur un formulaire.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la conception de modèles pour le service BDC dans SharePoint, consultez les rubriques suivantes :

- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Comment : ajouter une méthode de](../sharepoint/how-to-add-an-updater-method.md)mise à jour.
- [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Voir aussi

[Concevoir un modèle](../sharepoint/designing-a-business-data-connectivity-model.md) 
 de connectivité de données métiers [Créer un modèle](../sharepoint/creating-a-business-data-connectivity-model.md) 
 de connectivité de données métiers [Vue d’ensemble](../sharepoint/bdc-model-design-tools-overview.md) 
 des outils de conception de modèle BDC [Intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
