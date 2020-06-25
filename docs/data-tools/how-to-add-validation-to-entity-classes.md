---
title: Guide pratique pour ajouter une validation à des classes d’entité
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5d408c67b2e54fecd6404bac93d93ecfb35de162
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282343"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Guide pratique pour ajouter une validation à des classes d’entité
La *validation* de classes d’entité est le processus qui consiste à valider que les valeurs entrées dans des objets de données sont conformes aux contraintes du schéma d’un objet et également aux règles établies pour l’application. Il est conseillé de valider les données avant d'envoyer des mises à jour à la base de données sous-jacente pour réduire les erreurs. Une telle validation permet aussi de réduire le nombre potentiel d'allers-retours entre une application et la base de données.

Les [outils de LINQ to SQL dans Visual Studio fournissent des](../data-tools/linq-to-sql-tools-in-visual-studio2.md) méthodes partielles qui permettent aux utilisateurs d’étendre le code généré par le concepteur qui s’exécute pendant les insertions, les mises à jour et les suppressions d’entités complètes, ainsi que pendant et après les modifications de colonnes individuelles.

> [!NOTE]
> Cette rubrique fournit les étapes de base pour ajouter une validation à des classes d’entité à l’aide du **Concepteur O/R**. Étant donné qu’il peut être difficile de suivre ces étapes génériques sans faire référence à une classe d’entité spécifique, une procédure pas à pas qui utilise des données réelles est fournie.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Ajouter une validation pour les modifications apportées à la valeur dans une colonne spécifique
Cette procédure indique comment valider des données lorsque la valeur d'une colonne change. La validation est effectuée dans la définition de classe (plutôt que dans l’interface utilisateur) et, de ce fait, une exception est levée si la valeur provoque l’échec de la validation. Implémentez la gestion des erreurs pour le code de votre application qui essaie de modifier les valeurs de colonne.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Pour valider des données pendant la modification de valeur d'une colonne

1. Ouvrez ou créez un fichier de classes LINQ to SQL (fichier **. dbml** ) dans le **Concepteur O/R**. (Double-cliquez sur le fichier **.dbml** dans l’**Explorateur de solutions**.)

2. Dans le **Concepteur O/R**, cliquez avec le bouton droit sur la classe à laquelle vous souhaitez ajouter la validation, puis cliquez sur **Afficher le code**.

     Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.

3. Placez le curseur dans la classe partielle.

4. Pour les projets Visual Basic :

    1. Développez la liste **Nom de la méthode**.

    2. Localisez la méthode **OnCOLUMNNAMEChanging** pour la colonne concernée.

    3. Une méthode `OnCOLUMNNAMEChanging` est ajoutée à la classe partielle.

    4. Ajoutez le code suivant pour vérifier tout d'abord qu'une valeur a bien été entrée, puis pour garantir que la valeur entrée dans la colonne est acceptable dans votre application. L'argument `value` contient la valeur proposée. Vous devez donc ajouter la logique pour confirmer qu'il s'agit d'une valeur valide :

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Pour les projets C# :

    Comme les projets C# ne génèrent pas automatiquement de gestionnaires d’événements, vous pouvez utiliser IntelliSense pour créer les méthodes partielles de modification de colonne. Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles. Cliquez sur la méthode de modification de colonne de la colonne à laquelle la validation doit être ajoutée. Le code suivant ressemble au code généré lorsque vous sélectionnez une méthode partielle de modification de colonne :

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Ajouter une validation pour les mises à jour d’une classe d’entité
Outre la vérification des valeurs lors des modifications, vous avez la possibilité de valider les données lors d'une tentative de mise à jour d'une classe d'entité complète. La validation pendant une tentative de mise à jour vous permet de comparer des valeurs dans plusieurs colonnes si les règles métier le demandent. La procédure suivante indique comment effectuer la validation lors d'une tentative de mise à jour d'une classe d'entité complète.

> [!NOTE]
> Le code de validation pour les mises à jour des classes d’entité est exécuté dans la classe partielle <xref:System.Data.Linq.DataContext> (plutôt qu’en dehors de la classe partielle d’une classe d’entité spécifique).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Pour valider des données pendant une mise à jour de classe d'entité

1. Ouvrez ou créez un fichier de classes LINQ to SQL (fichier **. dbml** ) dans le **Concepteur O/R**. (Double-cliquez sur le fichier **.dbml** dans l’**Explorateur de solutions**.)

2. Cliquez avec le bouton droit sur une zone vide du **Concepteur O/R** et cliquez sur **Afficher le code**.

     Une classe partielle pour le `DataContext` s'ouvre dans l'éditeur de code.

3. Placez le curseur dans la classe partielle pour le `DataContext`.

4. Pour les projets Visual Basic :

    1. Développez la liste **Nom de la méthode**.

    2. Cliquez sur **UpdateENTITYCLASSNAME**.

    3. Une méthode `UpdateENTITYCLASSNAME` est ajoutée à la classe partielle.

    4. Accédez aux valeurs des colonnes individuelles à l’aide de l’argument `instance`, comme illustré par le code suivant :

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Pour les projets C# :

    Comme les projets C# ne génèrent pas automatiquement de gestionnaires d’événements, vous pouvez utiliser IntelliSense pour créer la `UpdateCLASSNAME` méthode partielle. Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles. Cliquez sur la méthode de mise à jour pour la classe sur laquelle vous souhaitez ajouter la validation. Le code suivant ressemble au code généré lorsque vous sélectionnez une `UpdateCLASSNAME` méthode partielle :

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Validation des données](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
