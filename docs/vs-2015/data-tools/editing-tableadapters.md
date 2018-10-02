---
title: Modifier des TableAdapters | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 995c1cfb5b125437847f364a01b66f3e551b8b4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507228"
---
# <a name="editing-tableadapters"></a>Modifier des TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Parfois, vous souhaiterez modifier le schéma de table de l’adaptateur. Pour ce faire, vous modifiez le principal de l’adaptateur `Fill` (méthode). Les TableAdapters sont créés avec une main `Fill` la méthode qui définit le schéma de la table de données associée. La principale `Fill` méthode est basée sur la requête ou procédure stockée que vous avez entré lorsque vous avez configuré à l’origine du TableAdapter ; il est la première méthode (plus élevée) sous la table de données sur le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Principale de toutes les modifications que vous apportez au TableAdapter `Fill` méthode sont reflétées dans le schéma de la table de données associée. Par exemple, suppression d’une colonne à partir de la requête dans le principal `Fill` méthode supprime également la colonne de la table de données associée. En outre, suppression de la colonne à partir de la main `Fill` méthode supprime la colonne de toutes les requêtes supplémentaires pour ce TableAdapter.  
  
 Vous pouvez utiliser la **Assistant Configuration de requêtes TableAdapter** pour créer et modifier des requêtes supplémentaires du TableAdapter. Ces requêtes supplémentaires doivent être conformes au schéma de table, sauf si elles retournent une valeur scalaire.  Les requêtes supplémentaires ont un nom que vous spécifiez (par exemple, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Pour démarrer l’Assistant de Configuration de requête TableAdapter avec une nouvelle requête  
  
1.  Ouvrez votre jeu de données dans le **Concepteur de Dataset**.  
  
2.  Si vous créez une nouvelle requête, faites glisser un **requête** de l’objet à partir de la **DataSet** onglet de la **boîte à outils** sur un <xref:System.Data.DataTable>, ou sélectionnez **ajouter une requête**à partir du menu contextuel du TableAdapter. Vous pouvez également faire glisser un **requête** objet dans une zone vide de la **Concepteur de Dataset**, ce qui crée un TableAdapter sans associé à un <xref:System.Data.DataTable>. Ces requêtes sont limitées à retourner des valeurs uniques (scalaires), ou l’exécution de mise à jour, insertion, ou supprimer des commandes sur la base de données. Pour plus d’informations, consultez [Comment : ajouter des requêtes globales à un TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  Sur le **choisir votre connexion de données** page, choisissez ou créez la connexion que la requête va utiliser.  
  
    > [!NOTE]
    >  Cette page s’affiche uniquement lorsque le concepteur ne peut pas déterminer la connexion appropriée à utiliser, ou lorsqu’aucune connexion n’est disponible.  
  
4.  Sur le **choisir un Type de commande** page, sélectionnez parmi les méthodes d’extraction de données à partir de la base de données suivantes :  
  
    -   **Utiliser des instructions SQL** vous permet de taper une instruction SQL pour sélectionner les données à partir de votre base de données.  
  
    -   **Créer la nouvelle procédure stockée** — Sélectionnez cette option pour que l’Assistant crée une nouvelle procédure stockée (dans la base de données) en fonction de l’instruction SELECT spécifiée.  
  
    -   **Utiliser des procédures stockées existantes** — Sélectionnez cette option pour exécuter une procédure stockée existante lors de l’exécution de la requête.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Pour démarrer l’Assistant Configuration de requête TableAdapter sur une requête existante  
  
-   Si vous modifiez une requête TableAdapter existante, avec le bouton droit de la requête, puis choisissez **configurer** dans le menu contextuel.  
  
    > [!NOTE]
    >  Clic droit sur la requête principale d’un TableAdapter reconfigure le TableAdapter et <xref:System.Data.DataTable> schéma, tandis qu’effectuant un clic droit sur un TableAdapter une requête supplémentaire uniquement configure la requête sélectionnée. Le **Assistant Configuration de TableAdapter** reconfigure la définition du TableAdapter ; le **Assistant Configuration de requêtes TableAdapter** reconfigure uniquement la requête sélectionnée.  
  
## <a name="running-the-wizard"></a>Exécution de l'Assistant  
 Faites glisser des requêtes sur le **Concepteur de Dataset**, ou configurez des requêtes existantes (toute requête répertoriée sous la première requête).  
  
 La première requête dans un TableAdapter est la requête principale du TableAdapter. Modification de cette requête principale ouvre le **Assistant Configuration de TableAdapter** et modifie le schéma de table de données du TableAdapter. Toutes les requêtes répertoriées sous la requête principale sont des requêtes supplémentaires et sont configurés à l’aide de la **Assistant Configuration de requêtes TableAdapter**. Pour plus d’informations sur l’exécution de l’Assistant, consultez [Comment : démarrer l’Assistant Configuration de requête TableAdapter](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Choisir votre connexion de données  
 Choisissez une connexion existante à partir de la liste des connexions ou cliquez sur **nouvelle connexion** pour créer une connexion à votre base de données.  
  
 À l’achèvement de la **propriétés de connexion** boîte de dialogue, le **détails de connexion** zone affiche des informations en lecture seule sur le fournisseur sélectionné, ainsi que la chaîne de connexion.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Enregistrer la chaîne de connexion dans le fichier de configuration de l'application  
 Choisissez **Oui, enregistrer la connexion en tant que** pour stocker la chaîne de connexion dans le fichier de configuration d’application. Tapez un nom pour la connexion ou utilisez le nom fourni par défaut.  
  
 L'enregistrement de chaînes de connexion dans le fichier de configuration de l'application simplifie le processus de gestion de votre application en cas de modification de la connexion de base de données. En cas de modification de la connexion de base de données, vous pouvez modifier la chaîne de connexion dans le fichier de configuration de l'application. Ainsi, vous n'avez pas besoin de modifier le code source et de recompiler votre application. Pour plus d’informations sur la modification d’une chaîne de connexion dans le fichier de configuration d’application, consultez [Comment : enregistrer et modifier des chaînes de connexion](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  Les informations sont stockées dans le fichier de configuration de l'application sous forme de texte brut. Pour réduire le risque d'accès non autorisé à des informations sensibles, pensez à chiffrer vos données. Pour plus d’informations, consultez [chiffrement et déchiffrement de données](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>Utiliser des instructions SQL  
 Cette section explique comment effectuer la **Assistant Configuration de requêtes TableAdapter** lors de la sélection du **utiliser des instructions SQL** option.  
  
## <a name="choose-a-query-type"></a>Choisir un type de requête  
 L'Assistant crée plusieurs types de requêtes en fonction des conditions requises de votre application. Vous pouvez choisir des requêtes SELECT qui retournent des lignes de données (une table de données) ou des requêtes SELECT qui retournent une valeur scalaire (une valeur unique telle que `Count` ou `Sum`).  
  
 Sur le **choisir un Type de requête** , sélectionnez le type de requête pour créer à partir de la liste des requêtes disponibles.  
  
> [!NOTE]
>  La création d'une instruction INSERT, UPDATE ou DELETE ne remplace pas les commandes de TableAdapter utilisées pour appeler la méthode `Update` de TableAdapter. Par exemple, si vous sélectionnez UPDATE comme type de requête, vous créez une requête avec un nom que vous spécifiez plus tard dans l'Assistant. Vous exécutez cette requête en appelant cette méthode nommée du TableAdapter. L'appel de la méthode `Update` de TableAdapter exécute les instructions créées au moment de la configuration du TableAdapter d'origine.  
  
## <a name="specify-a-sql-query-type-statement"></a>Spécifiez une instance SQL \<Type de requête > instruction  
 Sur le **spécifiez une instruction SQL** , tapez l’instruction SQL à exécuter lors de l’appel de la requête.  
  
> [!TIP]
>  L’Assistant fournit l’accès à la **Générateur de requêtes**, un outil visuel pour créer des requêtes SQL. Pour l’ouvrir, cliquez sur le **Générateur de requêtes** bouton.  
  
## <a name="choose-methods-to-generate"></a>Choisir les méthodes à générer  
 Cette page présente les options permettant de sélectionner les méthodes que l'Assistant génère pour la requête.  
  
 **Remplir un DataTable**  
 Crée une méthode pour remplir la table de données. Vous passez le nom de la table de données en tant que paramètre quand vous appelez cette méthode pour remplir la table de données avec les données retournées.  
  
 Si vous le souhaitez, vous pouvez modifier le nom par défaut dans le **nom de la méthode** boîte. Le choix d'un nom significatif peut être utile quand vous utilisez cette requête dans du code.  
  
 **Retourner un DataTable**  
 Crée une méthode pour retourner une table de données remplie. Dans certaines applications, il semble plus judicieux de retourner une table de données remplie plutôt que de remplir la table de données existante avec des données.  
  
 Si vous le souhaitez, vous pouvez modifier le nom par défaut dans le **nom de la méthode** boîte.  
  
## <a name="choose-function-name"></a>Choisir le nom de la fonction  
 Tapez un nom pour la fonction. La création d'une requête TableAdapter ajoute une méthode au TableAdapter avec le nom fourni ici. Appelez cette méthode pour exécuter la requête. Le choix d'un nom significatif est utile quand vous utilisez cette requête dans du code.  
  
> [!NOTE]
>  Quand vous créez des procédures stockées, vous devez fournir deux noms. Le premier nom désigne la procédure stockée créée dans la base de données, le deuxième nom désigne la méthode sur le TableAdapter qui exécute la procédure stockée quand elle est appelée.  
  
## <a name="create-new-stored-procedures"></a>Créer des procédures stockées  
 Cette section explique comment effectuer la **Assistant Configuration de requêtes TableAdapter** lors de la sélection du **créer des procédures stockées** option.  
  
1.  Dans le **générer les procédures stockées** , tapez l’instruction SQL à exécuter lors de l’appel de la procédure stockée.  
  
    > [!NOTE]
    >  L’Assistant fournit l’accès à la **Générateur de requêtes**, un outil visuel pour créer des requêtes SQL. Pour l’ouvrir, cliquez sur le **Générateur de requêtes** bouton.  
  
2.  Dans le **créer les procédures stockées** page, procédez comme suit :  
  
    1.  Tapez un nom pour la nouvelle procédure stockée.  
  
    2.  Choisissez de créer ou non la procédure stockée dans la base de données sous-jacente.  
  
        > [!NOTE]
        >  La possibilité de créer une procédure stockée dans la base de données est déterminée par les paramètres de sécurité pour la base de données spécifique.  
  
     Le **résultats de l’Assistant vue** page affiche les résultats de la création de la requête TableAdapter. Si l'Assistant rencontre des problèmes, cette page propose des informations sur l'erreur.  
  
## <a name="use-existing-stored-procedures"></a>Utiliser des procédures stockées existantes  
 Cette section explique comment effectuer la **Assistant Configuration de requêtes TableAdapter** lors de la sélection du **utiliser des procédures stockées existantes** option.  
  
1.  Sélectionnez une procédure stockée existante dans la liste déroulante sur le **choisir une procédure stockée existante** page de l’Assistant.  
  
     Le **paramètres** et **résultats** pour stockées sélectionné procédure sont affichés pour référence.  
  
2.  Cliquez sur **Suivant**.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Choisir la forme des données retournées par la procédure stockée  
 Le type des données retournées par la procédure stockée sélectionnée détermine la façon dont l'Assistant crée les méthodes TableAdapter.  
  
 Sélectionnez le type des données retournées par cette requête.  
  
-   En sélectionnant **données tabulaires** ouvre le **choisir les méthodes à générer** page (précédemment décrite dans cette page d’aide), qui vous permet de spécifier les types de méthodes, les noms de méthode et prise en charge la pagination à créer.  
  
-   En sélectionnant **une seule valeur** crée une méthode typée qui retourne une valeur unique. Cette option ouvre le **choisir un nom de fonction** page (précédemment décrite dans cette page d’aide).  
  
-   En sélectionnant **aucune valeur** crée une méthode typée qui exécute la procédure stockée et n’attend aucune donnée à renvoyer. Cette option ouvre le **choisir un nom de fonction** page (précédemment décrite dans cette page d’aide).  
  
## <a name="view-wizards-results"></a>Afficher les résultats de l'Assistant  
 Le **résultats de l’Assistant vue** page affiche les résultats de la création de la requête TableAdapter. Si l'Assistant rencontre des problèmes, les détails sont affichés dans cette page.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d’ensemble des Applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)