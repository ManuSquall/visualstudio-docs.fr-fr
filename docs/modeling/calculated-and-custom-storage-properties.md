---
title: Propriétés de stockage calculées et personnalisées
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f54589d70bc7cab3959d7f0a7ad2a84d3b028754
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877190"
---
# <a name="calculated-and-custom-storage-properties"></a>Propriétés de stockage calculées et personnalisées
Toutes les propriétés de domaine dans un langage spécifique à un domaine (DSL) peuvent être affichées à l’utilisateur sur le diagramme et dans votre Explorateur de langage et sont accessibles par le code de programme. Toutefois, les propriétés diffèrent dans la manière dont leurs valeurs sont stockées.

## <a name="kinds-of-domain-properties"></a>Types de propriétés de domaine
 Dans la définition DSL, vous pouvez définir le **type** d’une propriété de domaine, comme indiqué dans le tableau suivant :

|Type de propriété de domaine|Description|
|-|-|
|**Standard** (par défaut)|Une propriété de domaine qui est enregistrée dans le *stocker* et il est sérialisé vers le fichier.|
|**Calculé**|Une propriété de domaine en lecture seule qui n’est pas enregistrée dans le magasin, mais est calculée à partir d’autres valeurs.<br /><br /> Par exemple, `Person.Age` peut être calculé à partir de `Person.BirthDate`.<br /><br /> Vous devez fournir le code qui effectue le calcul. En règle générale, vous calculez la valeur à partir d’autres propriétés de domaine. Toutefois, vous pouvez également utiliser des ressources externes.|
|**Stockage personnalisé**|Une propriété de domaine qui n’est pas enregistrée directement dans le magasin, mais peut être à la fois get et set.<br /><br /> Vous devez fournir les méthodes obtenir et définir la valeur.<br /><br /> Par exemple, `Person.FullAddress` pourraient être stockées dans `Person.StreetAddress`, `Person.City`, et `Person.PostalCode`.<br /><br /> Vous pouvez également accéder à des ressources externes, par exemple, pour obtenir et définir des valeurs d’une base de données.<br /><br /> Votre code ne doit pas définir des valeurs dans le magasin lorsque `Store.InUndoRedoOrRollback` a la valeur true. Consultez [Transactions et les Setters personnalisés](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>En fournissant le code pour une propriété de stockage calculées ou personnalisé
 Si vous définissez le type d’une propriété de domaine sur calculé ou le stockage personnalisé, vous devez fournir des méthodes d’accès. Lorsque vous générez votre solution, un rapport d’erreurs vous indique ce qui est nécessaire.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Pour définir une Calculated ou la propriété de stockage personnalisé

1.  Dans DslDefinition.dsl, sélectionnez la propriété de domaine dans le diagramme ou dans **Explorateur DSL**.

2.  Dans le **propriétés** fenêtre, définissez la **type** champ **Calculated** ou **personnalisé stockage**.

     Assurez-vous que vous avez également défini son **Type** ce que vous souhaitez.

3.  Cliquez sur **transformer tous les modèles** dans la barre d’outils de **l’Explorateur de solutions**.

4.  Dans le menu **Générer** , cliquez sur **Générer la solution**.

     Vous recevez le message d’erreur suivant : «*Votre_classe* ne contient pas de définition pour Get*YourProperty*. »

5.  Double-cliquez sur le message d’erreur.

     Dsl\GeneratedCode\DomainClasses.cs ou DomainRelationships.cs s’ouvre. Au-dessus de l’appel de méthode en surbrillance, un commentaire vous invite à fournir une implémentation pour Get*YourProperty*().

    > [!NOTE]
    >  Ce fichier est généré à partir de DslDefinition.dsl. Si vous modifiez ce fichier, vos modifications seront perdues la prochaine fois que vous cliquez sur **transformer tous les modèles**. Au lieu de cela, ajoutez la méthode nécessaire dans un fichier distinct.

6.  Créez ou ouvrez un fichier de classe dans un dossier distinct, par exemple CustomCode\\*YourDomainClass*. cs.

     Assurez-vous que l’espace de noms est le même que dans le code généré.

7.  Dans le fichier de classe, écrivez une implémentation partielle de la classe de domaine. Dans la classe, écrire une définition de champ manquant `Get` méthode qui ressemble à l’exemple suivant :

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8.  Si vous définissez **type** à **personnalisé stockage**, vous devrez également fournir un `Set` (méthode). Exemple :

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Votre code ne doit pas définir des valeurs dans le magasin lorsque `Store.InUndoRedoOrRollback` a la valeur true. Consultez [Transactions et les Setters personnalisés](#setters).

9. Générez et exécutez la solution.

10. Tester la propriété. Assurez-vous que vous essayez de **Annuler** et **de restauration par progression**.

##  <a name="setters"></a> Transactions et des méthodes setter personnalisée
 Dans la méthode Set de propriété de stockage de personnalisé, il est inutile d’ouvrir une transaction, car la méthode est généralement appelée dans une transaction active.

 Cependant, la méthode Set peut également être appelée si l’utilisateur appelle l’annulation ou rétablissement, ou si une transaction est en cours de restauration. Lorsque <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> a la valeur true, votre méthode Set doit se comporter comme suit :

- Il ne doit pas apporter des modifications dans le magasin, tels que l’attribution de valeurs à d’autres propriétés de domaine. Le Gestionnaire d’annulation sera définir leurs valeurs.

- Toutefois, il doit mettre à jour des ressources externes, telles que la base de données ou de contenu du fichier ou d’objets en dehors du magasin. Cela permet de garantir qu’ils sont conservés dans synchronism avec les valeurs dans le magasin.

  Exemple :

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

 Pour plus d’informations sur les transactions, consultez [navigation et la mise à jour un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Propriétés des propriétés de domaine](../modeling/properties-of-domain-properties.md)
- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)