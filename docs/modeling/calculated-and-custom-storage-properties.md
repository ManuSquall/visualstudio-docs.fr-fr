---
title: "Propriétés de stockage calculées et personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3d8749e87a25cc9243cf7e76a99b027975673ab4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="calculated-and-custom-storage-properties"></a>Propriétés de stockage calculées et personnalisées
Toutes les propriétés de domaine dans un langage spécifique à un domaine (DSL) peuvent être affichées à l’utilisateur sur le diagramme et dans l’Explorateur de votre langue et est accessible par du code de programme. Toutefois, les propriétés diffèrent dans la manière dont leurs valeurs sont stockées.  
  
## <a name="kinds-of-domain-properties"></a>Types de propriétés de domaine  
 Dans la définition DSL, vous pouvez définir le **type** d’une propriété de domaine, comme indiqué dans le tableau suivant :  
  
|Type de propriété de domaine|Description|  
|--------------------------|-----------------|  
|**Standard** (par défaut)|Une propriété de domaine qui est enregistrée dans le *stocker* et il est sérialisé vers le fichier.|  
|**Calculé**|Une propriété de domaine en lecture seule qui n’est pas enregistrée dans le magasin, mais est calculée à partir d’autres valeurs.<br /><br /> Par exemple, `Person.Age` peut être calculé à partir de `Person.BirthDate`.<br /><br /> Vous devez fournir le code qui effectue le calcul. En règle générale, vous calculez la valeur à partir d’autres propriétés du domaine. Toutefois, vous pouvez également utiliser des ressources externes.|  
|**Stockage personnalisé**|Une propriété de domaine qui n’est pas enregistrée directement dans le magasin, mais peut être get et set.<br /><br /> Vous devez fournir les méthodes get et set de la valeur.<br /><br /> Par exemple, `Person.FullAddress` peuvent être stockés dans `Person.StreetAddress`, `Person.City`, et `Person.PostalCode`.<br /><br /> Vous pouvez également accéder aux ressources externes, par exemple, pour obtenir et définir des valeurs d’une base de données.<br /><br /> Votre code ne doit pas définir des valeurs dans le magasin lorsque `Store.InUndoRedoOrRollback` a la valeur true. Consultez [Transactions et les méthodes setter personnalisé](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fournit le code pour une propriété calculée ou personnalisée de stockage  
 Si vous définissez le type d’une propriété de domaine pour calculé ou d’un stockage personnalisé, vous devez fournir des méthodes d’accès. Lorsque vous générez votre solution, un rapport d’erreurs vous indique ce qui est obligatoire.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Pour définir une calculée ou une propriété de stockage personnalisé  
  
1.  Dans DslDefinition.dsl, sélectionnez la propriété de domaine dans le diagramme ou dans **Explorateur DSL**.  
  
2.  Dans le **propriétés** , configurez la **type** au champ **calculé** ou **personnalisé stockage**.  
  
     Assurez-vous que vous avez également défini son **Type** de votre choix.  
  
3.  Cliquez sur **transformer tous les modèles** dans la barre d’outils de **l’Explorateur de solutions**.  
  
4.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Vous recevez le message d’erreur suivant : «*YourClass* ne contient pas de définition pour Get*YourProperty*. »  
  
5.  Double-cliquez sur le message d’erreur.  
  
     Dsl\GeneratedCode\DomainClasses.cs ou DomainRelationships.cs s’ouvre. Au-dessus de l’appel de méthode mis en surbrillance un commentaire vous invite à fournir une implémentation pour Get*YourProperty*().  
  
    > [!NOTE]
    >  Ce fichier est généré à partir de DslDefinition.dsl. Si vous modifiez ce fichier, vos modifications seront perdues la prochaine fois que vous cliquez sur **transformer tous les modèles**. Au lieu de cela, ajoutez la méthode nécessaire dans un fichier distinct.  
  
6.  Créez ou ouvrez un fichier de classe dans un dossier distinct, par exemple CustomCode\\*YourDomainClass*. cs.  
  
     Assurez-vous que l’espace de noms est le même que dans le code généré.  
  
7.  Dans le fichier de classe, écrivez une implémentation partielle de la classe de domaine. Dans la classe, écrivez une définition pour manquants `Get` méthode qui ressemble à l’exemple suivant :  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Si vous définissez **type** à **personnalisé stockage**, vous devez également fournir un `Set` (méthode). Exemple :  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Votre code ne doit pas définir des valeurs dans le magasin lorsque `Store.InUndoRedoOrRollback` a la valeur true. Consultez [Transactions et les méthodes setter personnalisé](#setters).  
  
9. Générez et exécutez la solution.  
  
10. La propriété de test. Assurez-vous que vous essayez de **Annuler** et **de restauration par progression**.  
  
##  <a name="setters"></a>Les transactions et les méthodes setter personnalisées  
 Dans la méthode Set de propriété de stockage personnalisé, il est inutile d’ouvrir une transaction, car la méthode est généralement appelée dans une transaction active.  
  
 Cependant, la méthode Set peut également être appelée si l’utilisateur appelle l’annulation ou restauration par progression, ou si une transaction est en cours de restauration. Lorsque <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> a la valeur true, votre méthode Set doit se comporter comme suit :  
  
-   Il ne doit pas apporter des modifications dans le magasin, tels que l’attribution de valeurs à d’autres propriétés de domaine. Le Gestionnaire d’annulation sera définir leurs valeurs.  
  
-   Toutefois, il doit mettre à jour des ressources externes, telles que la base de données ou le contenu du fichier ou les objets en dehors de la banque. Cela permet de garantir qu’ils sont conservés dans synchronism avec les valeurs dans le magasin.  
  
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
  
 Pour plus d’informations sur les transactions, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Propriétés de domaine](../modeling/properties-of-domain-properties.md)   
 [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)