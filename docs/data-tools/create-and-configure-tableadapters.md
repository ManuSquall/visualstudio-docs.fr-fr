---
title: Créer et configurer des TableAdapters
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 166b11eaa1e4899547e6bb0735b0a220adc6e694
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="create-and-configure-tableadapters"></a>Créer et configurer des TableAdapters
Les TableAdapters fournissent une communication entre votre application et une base de données. Ils se connectent à la base de données, les requêtes exécutées ou les procédures stockées et renvoient une nouvelles données de table ou de remplissage existant <xref:System.Data.DataTable> avec les données retournées. Les TableAdapters peuvent également envoyer des données mises à jour à partir de votre application dans la base de données.

Les TableAdapters sont créés pour vous lorsque vous effectuez l’une des actions suivantes :

-   Exécutez le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png) et sélectionnez le **base de données** ou **Service Web** type de source de données.

-   Faites glisser les objets de base de données à partir de **l’Explorateur de serveurs** dans les **Concepteur de Dataset**.

Vous pouvez également créer un nouveau TableAdapter et configurez-le avec une source de données en faisant glisser un TableAdapter à partir de la boîte à outils vers une zone vide dans le **Concepteur de Dataset** surface.

Pour une introduction aux TableAdapters, consultez [remplir des jeux de données à l’aide des TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Utilisez l’Assistant Configuration de TableAdapter
Exécutez le **Assistant Configuration de TableAdapter** pour créer ou modifier des TableAdapters et leurs DataTables associés. Vous pouvez configurer un TableAdapter existant en cliquant dessus dans le **Concepteur de Dataset**.

![raddata Assistant de Configuration de l’adaptateur de Table](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata Assistant de Configuration de l’adaptateur de Table")

Si vous faites glisser un TableAdapter à partir de la boîte à outils lorsque le **Concepteur de Dataset** est en cours se concentrer, l’Assistant démarre et vous permet de spécifier les données de source de TableAdapter des invites doivent se connecter à. Sur la page suivante, l’Assistant vous demande le type de commandes, elle doit utiliser pour communiquer avec la base de données, des instructions SQL ou procédures stockées. (Il n’apparaît pas si vous configurez un TableAdapter est déjà associé à une source de données.)

-   Vous pouvez créer une nouvelle procédure stockée dans la base de données sous-jacent, si vous disposez des autorisations appropriées pour la base de données. Si vous n’avez pas ces autorisations, il ne sera pas être une option.

-   Vous pouvez également choisir d’exécuter des procédures stockées existantes pour le **sélectionnez**, **insérer**, **mise à jour**, et **supprimer** commandes de la TableAdapter. La procédure stockée qui est affectée à la **mise à jour** commande, par exemple, est exécutée lorsque la `TableAdapter.Update()` méthode est appelée.

Mappez les paramètres de la procédure stockée sélectionnée aux colonnes correspondantes de la table de données. Par exemple, si votre procédure stockée accepte un paramètre nommé `@CompanyName` qu’il transmet à la `CompanyName` jeu de colonnes dans la table, la **colonne Source** de la `@CompanyName` paramètre `CompanyName`.

> [!NOTE]
>  La procédure stockée qui est affectée à la commande SELECT est exécutée en appelant la méthode du TableAdapter que vous nommez dans l’étape suivante de l’Assistant. La méthode par défaut est `Fill`, de sorte que le code est généralement utilisé pour exécuter la procédure SELECT est `TableAdapter.Fill(tableName)`. Si vous modifiez le nom par défaut à partir de `Fill`, remplacez `Fill` avec le nom vous affectez et remplacez « TableAdapter » par le nom réel du TableAdapter (par exemple, `CustomersTableAdapter`).

-   En sélectionnant le **créer des méthodes pour envoyer les mises à jour directement à la base de données** option revient à affecter la `GenerateDBDirectMethods` true à la propriété. L’option n’est pas disponible lorsque l’instruction SQL d’origine ne fournit pas de suffisamment d’informations ou de la requête n’est pas une requête modifiable. Cette situation peut se produire, par exemple, dans **joindre** requêtes et les requêtes qui retournent une valeur (scalaire) unique.

Le **Options avancées** dans l’Assistant permettent :
- Générer des instructions INSERT, UPDATE et DELETE en fonction de l’instruction SELECT qui est définie sur le **générer les instructions SQL** page
- Utiliser l'accès concurrentiel optimiste
- Spécifiez s’il faut actualiser la table de données après une insertion et d’exécutent des instructions de mise à jour

## <a name="configure-a-tableadapters-fill-method"></a>Configurer la méthode de remplissage d’un TableAdapter
Parfois vous pouvez modifier le schéma de la table du TableAdapter. Pour ce faire, vous modifiez les principale du TableAdapter `Fill` (méthode). Les TableAdapters sont créés avec un serveur principal `Fill` la méthode qui définit le schéma de la table de données associée. Le serveur principal `Fill` méthode est basée sur la requête ou la procédure stockée que vous avez entré lorsque vous avez configuré à l’origine du TableAdapter. Il s’agit de la première méthode (plus haute) sous la table de données dans le Concepteur de DataSet.

![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif "TableAdapter")

Les modifications que vous apportez au TableAdapter du principal `Fill` méthode sont répercutées dans le schéma de la table de données associée. Par exemple, suppression d’une colonne de la requête dans le principal `Fill` méthode supprime également la colonne de la table de données associée. En outre, suppression de la colonne à partir de la main `Fill` méthode supprime la colonne de toutes les requêtes supplémentaires pour ce TableAdapter.

Vous pouvez utiliser l’Assistant Configuration de requête TableAdapter pour créer et modifier des requêtes supplémentaires du TableAdapter. Ces requêtes supplémentaires doivent être conformes au schéma de table, sauf si elles retournent une valeur scalaire.  Chaque requête supplémentaire a un nom que vous spécifiez.

L’exemple suivant vous montre comment appeler une requête supplémentaire nommée `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Pour démarrer l’Assistant Configuration de requête TableAdapter avec une nouvelle requête

1.  Ouvrez votre dataset dans le **Concepteur de Dataset**.

2.  Si vous créez une nouvelle requête, faites glisser un **requête** de l’objet à partir de la **DataSet** onglet de la **boîte à outils** sur un <xref:System.Data.DataTable>, ou sélectionnez **ajouter une requête**à partir du menu de raccourci du TableAdapter. Vous pouvez également faire glisser un **requête** objet dans une zone vide de la **Concepteur de Dataset**, ce qui crée un TableAdapter sans associé à un <xref:System.Data.DataTable>. Ces requêtes peuvent uniquement retourner des valeurs (scalaires) uniques, ou exécution UPDATE, INSERT ou supprimer des commandes sur la base de données.

3.  Sur le **choisir votre connexion de données** écran, sélectionnez ou créez la connexion que la requête va utiliser.

    > [!NOTE]
    >  Cet écran s’affiche uniquement lorsque le concepteur ne peut pas déterminer la connexion appropriée à utiliser, ou lorsqu’aucune connexion n’est disponible.

4.  Sur le **choisir un Type de commande** écran, sélectionnez parmi les méthodes suivantes de l’extraction de données à partir de la base de données :

    -   **Utiliser des instructions SQL** vous permet de taper une instruction SQL pour sélectionner les données à partir de votre base de données.

    -   **Créer la nouvelle procédure stockée** permet de disposer de l’Assistant créer une nouvelle procédure stockée (dans la base de données) en fonction de l’instruction SELECT spécifiée.

    -   **Utiliser des procédures stockées existantes** vous permet d’exécuter une procédure stockée existante lors de l’exécution de la requête.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Pour démarrer l’Assistant Configuration de requête TableAdapter sur une requête existante

-   Si vous modifiez une requête TableAdapter existante, avec le bouton droit de la requête, puis choisissez **configurer** dans le menu contextuel.

    > [!NOTE]
    >  Clic droit sur la requête principale d’un TableAdapter reconfigure le TableAdapter et <xref:System.Data.DataTable> schéma. Clic droit sur une requête supplémentaire sur un TableAdapter, cependant, configure la requête sélectionnée uniquement. Le **Assistant Configuration de TableAdapter** reconfigure la définition du TableAdapter, tandis que l’Assistant Configuration de requête TableAdapter reconfigure la requête sélectionnée uniquement.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Pour ajouter une requête globale à un TableAdapter

-   *Requêtes globales* sont des requêtes SQL qui retournent une valeur (scalaire) unique ou aucune valeur. En règle générale, les fonctions globales effectuent des opérations de base de données telles que des insertions, mises à jour, supprime. Ils regroupent également des informations, telles qu’un nombre de clients dans une table ou le total des frais pour tous les éléments dans un ordre particulier.

     Vous ajoutez des requêtes globales en faisant glisser un **requête** à partir de l’objet le **DataSet** onglet de la **boîte à outils** dans une zone vide de la **le Concepteur de Dataset**.

-   Spécifiez une requête qui effectue la tâche souhaitée, par exemple, `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    >  En faisant glisser un **requête** de l’objet directement sur le **Concepteur de Dataset** crée une méthode qui retourne uniquement une valeur scalaire (unique). Alors que la requête ou la procédure stockée que vous sélectionnez peut retourner plus de valeur unique, la méthode qui est créée par l’Assistant retourne uniquement une valeur unique. Par exemple, la requête peut retourner la première colonne de la première ligne des données retournées.

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)