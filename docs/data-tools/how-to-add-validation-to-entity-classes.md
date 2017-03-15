---
title: "Proc&#233;dure&#160;: ajouter une validation &#224; des classes d&#39;entit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: ajouter une validation &#224; des classes d&#39;entit&#233;
La validation de classes d'*entité* est un processus qui consiste à valider les valeurs entrées dans des objets de données pour vérifier qu'ils se conforment aux contraintes du schéma d'un objet et également aux règles établies pour l'application.Il est conseillé de valider les données avant d'envoyer des mises à jour à la base de données sous\-jacente pour réduire les erreurs.Une telle validation permet aussi de réduire le nombre potentiel d'allers\-retours entre une application et la base de données.  
  
 Le [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit des méthodes partielles aux utilisateurs pour leur permettre d'étendre le code généré par le concepteur qui s'exécute pendant les insertions, mises à jour et suppressions d'entités complètes, et également pendant et après les modifications des colonnes individuelles.  
  
> [!NOTE]
>  Cette rubrique fournit les étapes de base pour ajouter une validation aux classes d'entité à l'aide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Ces étapes génériques risqueraient d'être difficiles à suivre sans faire référence à une classe d'entité spécifique. Une procédure pas à pas utilisant les données réelles est donc fournie.Pour les instructions détaillées pas à pas de configuration de la validation à l'aide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consultez [Procédure pas à pas : ajout d'une validation à des classes d'entité](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md).  
  
## Ajout d'une validation pour la modification d'une valeur dans une colonne spécifique  
 Cette procédure indique comment valider des données lorsque la valeur d'une colonne change.La validation est effectuée dans la définition de classe \(plutôt que dans l'interface utilisateur\) et, de ce fait, une exception est levée si la valeur provoque l'échec de la validation.Implémentez la gestion des erreurs pour le code de votre application qui essaie de modifier les valeurs de colonne.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour valider des données pendant la modification de valeur d'une colonne  
  
1.  Ouvrez ou créez un nouveau fichier de classes LINQ to SQL \(**.dbml** \) dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(Double\-cliquez sur le fichier **.dbml** dans l'**Explorateur de solutions**.\)  
  
2.  Dans le Concepteur O\/R, cliquez avec le bouton droit sur la classe à laquelle vous souhaitez ajouter la validation, puis cliquez sur **Afficher le code**.  
  
     Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.  
  
3.  Placez le curseur dans la classe partielle.  
  
4.  Pour les projets Visual Basic :  
  
    1.  Développez la liste **Nom de la méthode**.  
  
    2.  Localisez la méthode **On***COLUMNNAME***Changing** pour la colonne concernée.  
  
    3.  Une méthode `On`*COLUMNNAME*`Changing` est ajoutée à la classe partielle.  
  
    4.  Ajoutez le code suivant pour vérifier tout d'abord qu'une valeur a bien été entrée, puis pour garantir que la valeur entrée dans la colonne est acceptable dans votre application.L'argument `value` contient la valeur proposée. Vous devez donc ajouter la logique pour confirmer qu'il s'agit d'une valeur valide :  
  
        ```vb#  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     Pour les projets C\# :  
  
    1.  Comme les projets C\# ne génèrent pas automatiquement des gestionnaires d'événements, vous pouvez utiliser IntelliSense pour créer les méthodes partielles de modification de colonne.  
  
         Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles.Cliquez sur la méthode de modification de colonne de la colonne à laquelle la validation doit être ajoutée.Le code généré lorsque vous sélectionnez une méthode partielle de modification de colonne est comparable au suivant :  
  
        ```c#  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## Ajout d'une validation pour les mises à jour d'une classe d'entité  
 Outre la vérification des valeurs lors des modifications, vous avez la possibilité de valider les données lors d'une tentative de mise à jour d'une classe d'entité complète.La validation pendant une tentative de mise à jour vous permet de comparer des valeurs dans plusieurs colonnes si les règles métier le demandent.La procédure suivante indique comment effectuer la validation lors d'une tentative de mise à jour d'une classe d'entité complète.  
  
> [!NOTE]
>  Le code de validation pour les mises à jour des classes d'entité est exécuté dans la classe partielle <xref:System.Data.Linq.DataContext> \(plutôt qu'en dehors de la classe partielle d'une classe d'entité spécifique\).  
  
#### Pour valider des données pendant une mise à jour de classe d'entité  
  
1.  Ouvrez ou créez un nouveau fichier de classes LINQ to SQL \(**.dbml** \) dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(Double\-cliquez sur le fichier **.dbml** dans l'**Explorateur de solutions**.\)  
  
2.  Cliquez avec le bouton droit sur une zone vide du Concepteur O\/R et cliquez sur **Afficher le code**.  
  
     Une classe partielle pour le `DataContext` s'ouvre dans l'éditeur de code.  
  
3.  Placez le curseur dans la classe partielle pour le `DataContext`.  
  
4.  Pour les projets Visual Basic :  
  
    1.  Développez la liste **Nom de la méthode**.  
  
    2.  Cliquez sur **Mettre à jour***ENTITYCLASSNAME*.  
  
    3.  Une méthode `Update`*ENTITYCLASSNAME* est ajoutée à la classe partielle.  
  
    4.  Accédez aux valeurs des colonnes individuelles à l'aide de l'argument `instance`, comme illustré par le code suivant :  
  
        ```vb#  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     Pour les projets C\# :  
  
    1.  Comme les projets C\# ne génèrent pas automatiquement de gestionnaires d'événements, vous pouvez utiliser IntelliSense pour créer la méthode partielle `Update`*CLASSNAME*.  
  
    2.  Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles.Cliquez sur la méthode de mise à jour pour la classe concernée.Le code suivant ressemble au code généré lorsque vous sélectionnez méthode partielle `Update`*CLASSNAME* :  
  
        ```c#  
        partial void UpdateCLASSNAME(CLASSNAME instance)  
        {  
            if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
            {  
                string ErrorMessage = "Invalid data!";  
                throw new System.Exception(ErrorMessage);  
            }  
        }  
        ```  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Validation des données](../Topic/Validating%20Data.md)