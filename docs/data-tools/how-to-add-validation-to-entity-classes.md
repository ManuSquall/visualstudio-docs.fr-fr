---
title: 'Comment : ajouter la validation aux classes d’entité'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d102bdf20349d6bd4efdecd1c460f1e46646eb37
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089336"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Comment : ajouter la validation aux classes d’entité
*Validation* classes d’entité est le processus consistant à confirmer que les valeurs entrées dans des objets de données sont conformes avec les contraintes d’un schéma d’objet et également aux règles établies pour l’application. Il est conseillé de valider les données avant d'envoyer des mises à jour à la base de données sous-jacente pour réduire les erreurs. Une telle validation permet aussi de réduire le nombre potentiel d'allers-retours entre une application et la base de données.

 Le [des outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit des méthodes partielles qui permettent aux utilisateurs d’étendre le code généré par le concepteur qui s’exécute pendant les insertions, mises à jour et supprime des entités complètes et également pendant et après la colonne individuelle modifications.

> [!NOTE]
>  Cette rubrique fournit les étapes de base pour ajouter une validation aux classes d’entité à l’aide de la **Concepteur O/R**. Car il peut être difficile de suivre ces étapes génériques sans faire référence à une classe d’entité spécifique, une procédure pas à pas qui utilise des données réelles est fourni.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Ajouter la validation des modifications à la valeur dans une colonne spécifique
 Cette procédure indique comment valider des données lorsque la valeur d'une colonne change. Étant donné que la validation est effectuée à l’intérieur de la définition de classe (et non dans l’interface utilisateur), une exception est levée si la valeur fait échouer la validation. Implémentez la gestion des erreurs pour le code de votre application qui essaie de modifier les valeurs de colonne.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Pour valider des données pendant la modification de valeur d'une colonne

1.  Ouvrez ou créez un nouveau fichier LINQ to SQL Classes (**.dbml** fichier) dans le **Concepteur O/R**. (Double-cliquez sur le **.dbml** fichier **l’Explorateur de solutions**.)

2.  Dans le **Concepteur O/R**, avec le bouton droit de la classe pour laquelle vous souhaitez ajouter la validation, puis cliquez sur **afficher le Code**.

     Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.

3.  Placez le curseur dans la classe partielle.

4.  Pour les projets Visual Basic :

    1.  Développez le **nom de la méthode** liste.

    2.  Recherchez le **OnCOLUMNNAMEChanging** méthode pour la colonne que vous souhaitez ajouter la validation.

    3.  Un `OnCOLUMNNAMEChanging` méthode est ajoutée à la classe partielle.

    4.  Ajoutez le code suivant pour vérifier tout d'abord qu'une valeur a bien été entrée, puis pour garantir que la valeur entrée dans la colonne est acceptable dans votre application. L'argument `value` contient la valeur proposée. Vous devez donc ajouter la logique pour confirmer qu'il s'agit d'une valeur valide :

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Pour les projets C# :

    Étant donné que les projets c# ne génèrent pas automatiquement les gestionnaires d’événements, vous pouvez utiliser IntelliSense pour créer les méthodes partielles de modification de colonne. Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles. Cliquez sur la méthode de modification de colonne de la colonne à laquelle la validation doit être ajoutée. Le code suivant ressemble au code qui est généré lorsque vous sélectionnez une méthode partielle de modification de colonne :

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Ajouter la Validation des mises à jour à une classe d’entité
 Outre la vérification des valeurs lors des modifications, vous avez la possibilité de valider les données lors d'une tentative de mise à jour d'une classe d'entité complète. La validation pendant une tentative de mise à jour vous permet de comparer des valeurs dans plusieurs colonnes si les règles métier le demandent. La procédure suivante indique comment effectuer la validation lors d'une tentative de mise à jour d'une classe d'entité complète.

> [!NOTE]
>  Le code de validation pour les mises à jour des classes d'entité est exécuté dans la classe partielle <xref:System.Data.Linq.DataContext> (plutôt qu'en dehors de la classe partielle d'une classe d'entité spécifique).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Pour valider des données pendant une mise à jour de classe d'entité

1.  Ouvrez ou créez un nouveau fichier LINQ to SQL Classes (**.dbml** fichier) dans le **Concepteur O/R**. (Double-cliquez sur le **.dbml** fichier **l’Explorateur de solutions**.)

2.  Cliquez sur une zone vide sur le **Concepteur O/R** et cliquez sur **afficher le Code**.

     Une classe partielle pour le `DataContext` s'ouvre dans l'éditeur de code.

3.  Placez le curseur dans la classe partielle pour le `DataContext`.

4.  Pour les projets Visual Basic :

    1.  Développez le **nom de la méthode** liste.

    2.  Cliquez sur **UpdateENTITYCLASSNAME**.

    3.  Un `UpdateENTITYCLASSNAME` méthode est ajoutée à la classe partielle.

    4.  Accédez aux valeurs des colonnes individuelles à l'aide de l'argument `instance`, comme illustré par le code suivant :

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Pour les projets C# :

    Étant donné que les projets c# ne génèrent pas automatiquement les gestionnaires d’événements, vous pouvez utiliser IntelliSense pour créer le partielle `UpdateCLASSNAME` (méthode). Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles. Cliquez sur la méthode de mise à jour pour la classe sur laquelle vous souhaitez ajouter la validation. Le code suivant ressemble au code qui est généré lorsque vous sélectionnez un `UpdateCLASSNAME` méthode partielle :

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