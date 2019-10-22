---
title: Créer et configurer des TableAdapters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a2136960dfcbbbcf63fbefeb16d527793d4b939
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631040"
---
# <a name="create-and-configure-tableadapters"></a>Créer et configurer des TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les TableAdapters assurent la communication entre votre application et une base de données. Ils se connectent à la base de données, exécutent des requêtes ou des procédures stockées, puis renvoient une nouvelle table de données ou remplissent un <xref:System.Data.DataTable> existant avec les données retournées. Les TableAdapters peuvent également renvoyer des données mises à jour de votre application vers la base de données.

 Les TableAdapters sont créés pour vous lorsque vous effectuez l’une des actions suivantes :

- Exécutez l' [Assistant Configuration de source de données](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) et sélectionnez la **base de** données ou le type de source de données du **service Web** .

- Faites glisser des objets de base de données à partir de [Explorateur de serveurs](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) vers le **Concepteur de DataSet**.

  Vous pouvez créer un nouveau TableAdapter et le configurer avec une source de données en faisant glisser un TableAdapter de la boîte à outils vers une zone vide de la surface de **Concepteur de DataSet** .

  Pour une introduction aux TableAdapters, consultez [remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Utiliser l’Assistant Configuration de TableAdapter
 Exécutez l' **Assistant Configuration de TableAdapter** pour créer ou modifier des TableAdapters et leurs DataTables associés. Vous pouvez configurer un TableAdapter existant en cliquant dessus avec le bouton droit dans la **Concepteur de DataSet**.

 ![Assistant Configuration de l’adaptateur de table raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "Assistant Configuration de l’adaptateur de table raddata")

 Si vous faites glisser un nouveau TableAdapter à partir de la boîte à outils lorsque le **Concepteur de DataSet** est activé, l’Assistant vous invite à spécifier la source de données à laquelle le TableAdapter doit se connecter, ainsi que le type de commandes qu’il doit utiliser pour communiquer avec la base de données, SQL des instructions ou des procédures stockées. Vous ne le verrez pas si vous configurez un TableAdapter qui est déjà associé à une source de données.

- L’utilisation des **méthodes Create pour envoyer des mises à jour directement à l’option de base de données** revient à affecter la valeur true à la propriété `GenerateDBDirectMethods`. L’option n’est pas disponible quand l’instruction SQL d’origine ne fournit pas assez d’informations ou que la requête ne peut pas être mise à jour. Cette situation peut se produire, par exemple, dans les requêtes **join** et les requêtes qui retournent une valeur unique (scalaire).

- Vous avez la possibilité de créer une procédure stockée dans la base de données sous-jacente si vous disposez des autorisations appropriées pour la base de données. Si vous ne disposez pas de ces autorisations, ce n’est pas une option.

- Vous pouvez également choisir d’exécuter des procédures stockées existantes pour les commandes **Select**, **Insert**, **Update**et **Delete** du TableAdapter. La procédure stockée qui est assignée à la commande **Update** , par exemple, est exécutée lorsque la méthode `TableAdapter.Update()` est appelée.

     Mappez les paramètres de la procédure stockée sélectionnée aux colonnes correspondantes de la table de données. Par exemple, si votre procédure stockée accepte un paramètre nommé `@CompanyName` qu’elle passe à la colonne `CompanyName` de la table, définissez la **colonne source** du paramètre `@CompanyName` sur `CompanyName`.

    > [!NOTE]
    > La procédure stockée qui est assignée à la commande SELECT est exécutée en appelant la méthode du TableAdapter que vous nommez à l’étape suivante de l’Assistant. La méthode par défaut est `Fill`. le code généralement utilisé pour exécuter la procédure SELECT est donc `TableAdapter.Fill(tableName)`. Si vous remplacez le nom par défaut `Fill`, remplacez `Fill` par le nom que vous attribuez, et remplacez « TableAdapter » par le nom réel du TableAdapter (par exemple, `CustomersTableAdapter`).

- Les **Options avancées** de l’Assistant vous permettent de générer des instructions INSERT, Update et Delete en fonction de l’instruction SELECT définie dans la page **générer des instructions SQL** . Utilisez l’accès concurrentiel optimiste et spécifiez s’il faut actualiser la table de données après l’exécution des instructions INSERT et UPDATE.

## <a name="configure-a-tableadapters-fill-method"></a>Configurer la méthode Fill d’un TableAdapter
 Parfois, vous souhaiterez peut-être modifier le schéma de la table du TableAdapter. Pour ce faire, vous devez modifier la méthode `Fill` principale du TableAdapter. Les TableAdapters sont créés avec une méthode de `Fill` primaire qui définit le schéma de la table de données associée. La méthode de `Fill` primaire est basée sur la requête ou la procédure stockée que vous avez entrée lors de la configuration initiale du TableAdapter. Il s’agit de la première méthode (la plus en haut) sous la table de données dans le concepteur de DataSet.

 ![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif "TableAdapter")

 Toutes les modifications que vous apportez à la méthode principale de `Fill` du TableAdapter sont reflétées dans le schéma de la table de données associée. Par exemple, la suppression d’une colonne de la requête dans la méthode principale `Fill` supprime également la colonne de la table de données associée. En outre, la suppression de la colonne de la méthode main `Fill` supprime la colonne de toutes les requêtes supplémentaires pour ce TableAdapter.

 Vous pouvez utiliser l’Assistant Configuration de requêtes TableAdapter pour créer et modifier des requêtes supplémentaires pour le TableAdapter. Ces requêtes supplémentaires doivent être conformes au schéma de la table, à moins qu’elles ne retournent une valeur scalaire.  Les requêtes supplémentaires ont un nom que vous spécifiez (par exemple, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Pour démarrer l’Assistant Configuration de requêtes TableAdapter avec une nouvelle requête

1. Ouvrez votre dataset dans le **Concepteur de DataSet**.

2. Si vous créez une nouvelle requête, faites glisser un objet **requête** de l’onglet **DataSet** de la **boîte à outils** vers un <xref:System.Data.DataTable> ou sélectionnez Ajouter une **requête** dans le menu contextuel du TableAdapter. Vous pouvez également faire glisser un objet de **requête** dans une zone vide du **Concepteur de DataSet**, ce qui crée un TableAdapter sans <xref:System.Data.DataTable> associé. Ces requêtes peuvent retourner des valeurs uniques (scalaires) ou exécuter des commandes UPDATE, INSERT ou DELETE sur la base de données.

3. Dans l’écran **choisir votre connexion de données** , sélectionnez ou créez la connexion que la requête doit utiliser.

    > [!NOTE]
    > Cet écran s’affiche uniquement lorsque le concepteur ne peut pas déterminer la connexion appropriée à utiliser ou lorsqu’aucune connexion n’est disponible.

4. Dans l’écran **choisir un type de commande** , sélectionnez l’une des méthodes suivantes pour extraire des données de la base de données :

    - L’option **utiliser des instructions SQL** vous permet de taper une instruction SQL pour sélectionner les données de votre base de données.

    - **Créer une nouvelle procédure stockée** vous permet de demander à l’Assistant de créer une nouvelle procédure stockée (dans la base de données) en fonction de l’instruction SELECT spécifiée.

    - **Utiliser des procédures stockées existantes** vous permet d’exécuter une procédure stockée existante lors de l’exécution de la requête.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Pour démarrer l’Assistant Configuration de requêtes TableAdapter sur une requête existante

- Si vous modifiez une requête TableAdapter existante, cliquez avec le bouton droit sur la requête, puis choisissez **configurer** dans le menu contextuel.

    > [!NOTE]
    > Cliquez avec le bouton droit sur la requête principale d’un TableAdapter pour reconfigurer le schéma du TableAdapter et du <xref:System.Data.DataTable>. Toutefois, si vous cliquez avec le bouton droit sur une requête supplémentaire sur un TableAdapter, cela ne configure que la requête sélectionnée. L' **Assistant Configuration de TableAdapter** reconfigure la définition de TableAdapter, tandis que l’Assistant Configuration de requêtes TableAdapter reconfigure la requête sélectionnée uniquement.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Pour ajouter une requête globale à un TableAdapter

- Les *requêtes globales* sont des requêtes SQL qui retournent une valeur unique (scalaire) ou aucune valeur. En règle générale, les fonctions globales effectuent des opérations de base de données telles que les insertions, les mises à jour, les suppressions. Ils agrègent également des informations, telles que le nombre de clients dans une table ou le montant total des frais pour tous les articles dans un ordre particulier.

     Pour ajouter des requêtes globales, faites glisser un objet de **requête** de l’onglet **DataSet** de la **boîte à outils** vers une zone vide du **Concepteur de DataSet**.

- Fournissez une requête qui effectue la tâche souhaitée, par exemple, `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    > Le fait de faire glisser un objet de **requête** directement sur le **Concepteur de DataSet** crée une méthode qui retourne uniquement une valeur scalaire (unique). Alors que la requête ou la procédure stockée que vous sélectionnez peut retourner plus d’une valeur unique, la méthode créée par l’Assistant ne retourne qu’une seule valeur. Par exemple, la requête peut retourner la première colonne de la première ligne des données retournées.

## <a name="see-also"></a>Voir aussi
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
