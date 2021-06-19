---
title: Propriétés de stockage calculées et personnalisées
description: Découvrez comment les propriétés de domaine d’un langage spécifique à un domaine (DSL) peuvent être affichées à l’utilisateur sur le diagramme et dans l’Explorateur de langage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98dca6759b9e4a77e71139b6d9ec9b394d99b04
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385420"
---
# <a name="calculated-and-custom-storage-properties"></a>Propriétés de stockage calculées et personnalisées
Toutes les propriétés de domaine dans un langage spécifique à un domaine (DSL) peuvent être affichées à l’utilisateur sur le diagramme et dans l’Explorateur de langage, et être accessibles par le code du programme. Toutefois, les propriétés diffèrent dans la façon dont leurs valeurs sont stockées.

## <a name="kinds-of-domain-properties"></a>Types de propriétés de domaine
 Dans la définition DSL, vous pouvez définir le **type** d’une propriété de domaine, comme indiqué dans le tableau suivant :

|Genre de propriété de domaine|Description|
|-|-|
|**Standard** (par défaut)|Propriété de domaine enregistrée dans le *magasin* et sérialisée dans un fichier.|
|**Calculées**|Propriété de domaine en lecture seule qui n’est pas enregistrée dans le magasin, mais qui est calculée à partir d’autres valeurs.<br /><br /> Par exemple, `Person.Age` peut être calculé à partir de `Person.BirthDate` .<br /><br /> Vous devez fournir le code qui effectue le calcul. En règle générale, vous calculez la valeur à partir d’autres propriétés de domaine. Toutefois, vous pouvez également utiliser des ressources externes.|
|**Stockage personnalisé**|Propriété de domaine qui n’est pas enregistrée directement dans le magasin, mais qui peut être à la fois obtenue et définie.<br /><br /> Vous devez fournir les méthodes qui obtiennent et définissent la valeur.<br /><br /> Par exemple, `Person.FullAddress` peut être stocké dans `Person.StreetAddress` , `Person.City` et `Person.PostalCode` .<br /><br /> Vous pouvez également accéder à des ressources externes, par exemple pour obtenir et définir des valeurs à partir d’une base de données.<br /><br /> Votre code ne doit pas définir de valeurs dans le magasin lorsque la `Store.InUndoRedoOrRollback` propriété a la valeur true. Consultez [transactions et méthodes setter personnalisées](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fourniture du code pour une propriété de stockage calculée ou personnalisée
 Si vous définissez le type d’une propriété de domaine sur stockage calculé ou personnalisé, vous devez fournir des méthodes d’accès. Lorsque vous générez votre solution, un rapport d’erreurs vous indique ce qui est requis.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Pour définir une propriété de stockage calculée ou personnalisée

1. Dans DslDefinition. DSL, sélectionnez la propriété de domaine dans le diagramme ou dans l' **Explorateur DSL**.

2. Dans la fenêtre **Propriétés** , définissez le champ **genre** sur stockage **calculé** ou **personnalisé**.

     Assurez-vous que vous avez également défini son **type** comme vous le souhaitez.

3. Cliquez sur **transformer tous les modèles** dans la barre d’outils de **Explorateur de solutions**.

4. Dans le menu **Générer**, cliquez sur **Générer la solution**.

     Vous recevez le message d’erreur suivant : «*YourClass* ne contient pas de définition pour obtenir *YourProperty*».

5. Double-cliquez sur le message d’erreur.

     Dsl\GeneratedCode\DomainClasses.cs ou DomainRelationships. cs s’ouvre. Au-dessus de l’appel de méthode en surbrillance, un commentaire vous invite à fournir une implémentation pour obtenir *YourProperty*().

    > [!NOTE]
    > Ce fichier est généré à partir de DslDefinition. DSL. Si vous modifiez ce fichier, vos modifications seront perdues la prochaine fois que vous cliquerez sur **transformer tous les modèles**. Au lieu de cela, ajoutez la méthode requise dans un fichier séparé.

6. Créez ou ouvrez un fichier de classe dans un dossier séparé, par exemple CustomCode \\ *YourDomainClass*. cs.

     Assurez-vous que l’espace de noms est le même que dans le code généré.

7. Dans le fichier de classe, écrivez une implémentation partielle de la classe de domaine. Dans la classe, écrivez une définition pour la méthode manquante `Get` qui ressemble à l’exemple suivant :

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Si vous définissez **type** sur **stockage personnalisé**, vous devrez également fournir une `Set` méthode. Exemple :

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Votre code ne doit pas définir de valeurs dans le magasin lorsque la `Store.InUndoRedoOrRollback` propriété a la valeur true. Consultez [transactions et méthodes setter personnalisées](#setters).

9. Créez et exécutez la solution.

10. Testez la propriété. Veillez à essayer les opérations d' **annulation** et de **rétablissement**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transactions et méthodes setter personnalisées
 Dans la méthode Set de la propriété de stockage personnalisé, il n’est pas nécessaire d’ouvrir une transaction, car la méthode est généralement appelée à l’intérieur d’une transaction active.

 Toutefois, la méthode Set peut également être appelée si l’utilisateur appelle Undo ou Redo, ou si une transaction est en cours de restauration. Lorsque <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> a la valeur true, votre méthode Set doit se comporter comme suit :

- Elle ne doit pas apporter de modifications au magasin, telles que l’affectation de valeurs à d’autres propriétés de domaine. Le gestionnaire d’annulation définit leurs valeurs.

- Toutefois, il doit mettre à jour toutes les ressources externes, telles que le contenu d’une base de données ou d’un fichier, ou des objets en dehors du magasin. Cela permet de s’assurer qu’ils sont conservés dans synchroniser avec les valeurs du magasin.

  Exemple :

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 Pour plus d’informations sur les transactions, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Propriétés des propriétés de domaine](../modeling/properties-of-domain-properties.md)
- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)
