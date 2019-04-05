---
title: 'Procédure : Ajouter une validation aux classes d’entité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3c08dbb66e71cc1fd362279ae33006c20e11436
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949592"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Procédure : Ajouter une validation à des classes d’entité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La *validation* de classes d’entité est le processus qui consiste à valider que les valeurs entrées dans des objets de données sont conformes aux contraintes du schéma d’un objet et également aux règles établies pour l’application. Il est conseillé de valider les données avant d'envoyer des mises à jour à la base de données sous-jacente pour réduire les erreurs. Une telle validation permet aussi de réduire le nombre potentiel d'allers-retours entre une application et la base de données.  
  
 Le [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit des méthodes partielles qui permettent aux utilisateurs d’étendre le code généré par le concepteur qui s’exécute pendant les insertions, mises à jour et supprime des entités complètes et également pendant et après la colonne individuelle modifications.  
  
> [!NOTE]
>  Cette rubrique fournit les étapes de base pour ajouter une validation aux classes d'entité à l'aide du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Ces étapes génériques risqueraient d'être difficiles à suivre sans faire référence à une classe d'entité spécifique. Une procédure pas à pas utilisant les données réelles est donc fournie.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Ajout d'une validation pour la modification d'une valeur dans une colonne spécifique  
 Cette procédure indique comment valider des données lorsque la valeur d'une colonne change. La validation est effectuée dans la définition de classe (plutôt que dans l'interface utilisateur) et, de ce fait, une exception est levée si la valeur provoque l'échec de la validation. Implémentez la gestion des erreurs pour le code de votre application qui essaie de modifier les valeurs de colonne.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>Pour valider des données pendant la modification de valeur d'une colonne  
  
1. Ouvrez ou créez un nouveau fichier LINQ to SQL Classes (**.dbml** fichier) dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Double-cliquez sur le fichier **.dbml** dans l’**Explorateur de solutions**.)  
  
2. Dans le Concepteur O/R, cliquez sur la classe pour laquelle vous souhaitez ajouter la validation, puis cliquez sur **afficher le Code**.  
  
    Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.  
  
3. Placez le curseur dans la classe partielle.  
  
4. Pour les projets Visual Basic :  
  
   1. Développez la liste **Nom de la méthode**.  
  
   2. Recherchez le **sur**_COLUMNNAME_**Changing** méthode pour la colonne que vous souhaitez ajouter la validation.  
  
   3. Un `On` *COLUMNNAME* `Changing` méthode est ajoutée à la classe partielle.  
  
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
  
   5. Comme les projets C# ne génèrent pas automatiquement des gestionnaires d'événements, vous pouvez utiliser IntelliSense pour créer les méthodes partielles de modification de colonne.  
  
       Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles. Cliquez sur la méthode de modification de colonne de la colonne à laquelle la validation doit être ajoutée. Le code généré lorsque vous sélectionnez une méthode partielle de modification de colonne est comparable au suivant :  
  
      ```csharp  
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
          {  
             throw new System.NotImplementedException();  
          }  
  
      ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>Ajout d'une validation pour les mises à jour d'une classe d'entité  
 Outre la vérification des valeurs lors des modifications, vous avez la possibilité de valider les données lors d'une tentative de mise à jour d'une classe d'entité complète. La validation pendant une tentative de mise à jour vous permet de comparer des valeurs dans plusieurs colonnes si les règles métier le demandent. La procédure suivante indique comment effectuer la validation lors d'une tentative de mise à jour d'une classe d'entité complète.  
  
> [!NOTE]
>  Le code de validation pour les mises à jour des classes d’entité est exécuté dans la classe partielle <xref:System.Data.Linq.DataContext> (plutôt qu’en dehors de la classe partielle d’une classe d’entité spécifique).  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Pour valider des données pendant une mise à jour de classe d'entité  
  
1. Ouvrez ou créez un nouveau fichier LINQ to SQL Classes (**.dbml** fichier) dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Double-cliquez sur le fichier **.dbml** dans l’**Explorateur de solutions**.)  
  
2. Avec le bouton droit sur le Concepteur O/R, une zone vide et cliquez sur **afficher le Code**.  
  
    Une classe partielle pour le `DataContext` s'ouvre dans l'éditeur de code.  
  
3. Placez le curseur dans la classe partielle pour le `DataContext`.  
  
4. Pour les projets Visual Basic :  
  
   1. Développez la liste **Nom de la méthode**.  
  
   2. Cliquez sur **mise à jour**_ENTITYCLASSNAME_.  
  
   3. Un `Update` *ENTITYCLASSNAME* méthode est ajoutée à la classe partielle.  
  
   4. Accédez aux valeurs des colonnes individuelles à l’aide de l’argument `instance`, comme illustré par le code suivant :  
  
      ```vb  
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
          Dim ErrorMessage As String = "Invalid data!"  
          Throw New Exception(ErrorMessage)  
      End If  
      ```  
  
      Pour les projets C# :  
  
   5. Étant donné que les projets c# ne génèrent pas automatiquement les gestionnaires d’événements, vous pouvez utiliser IntelliSense pour créer le partielle `Update` *CLASSNAME* (méthode).  
  
   6. Tapez `partial`, puis un espace pour accéder à la liste de méthodes partielles disponibles. Cliquez sur la méthode de mise à jour pour la classe concernée. Le code suivant ressemble au code qui est généré lorsque vous sélectionnez un `Update` *CLASSNAME* méthode partielle :  
  
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
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
