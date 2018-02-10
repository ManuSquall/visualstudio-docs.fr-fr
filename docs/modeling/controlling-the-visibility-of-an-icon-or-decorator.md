---
title: "Contrôle de la visibilité d’une icône ou d’un élément décoratif | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 835d9d356a06c831bb3decf6d0a5a6a4b5620302
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Contrôle de la visibilité d'une icône ou d'un élément décoratif
A *decorator* est une icône ou une ligne de texte qui apparaît sur la forme d’un langage spécifique à un domaine (DSL). Vous pouvez afficher l’élément décoratif et disparaissent en fonction de l’état des propriétés dans le modèle. Par exemple, sur une forme représentant une personne, vous pourriez avoir différentes icônes qui s’affichent en fonction du sexe de la personne, nombre d’enfants et ainsi de suite.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Contrôle de la visibilité d’une icône ou d’un élément décoratif  
 La procédure suivante suppose que vous avez déjà défini une forme et son mappage à une classe de domaine. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Pour contrôler la visibilité d’un decorator icône ou du texte  
  
1.  Dans le schéma de définition DSL, ajouter à la classe de forme, les icônes ou les éléments décoratifs de texte que vous souhaitez voir apparaître.  
  
    1.  Avec le bouton droit de la classe de forme, pointez sur **ajouter**, puis cliquez sur le type de decorator requis.  
  
    2.  Définir le decorator **Position** propriété. Plus d’un élément décoratif peut avoir la même position. Par exemple, vous pourriez avoir des icônes pour homme et Femme partage la même position.  
  
    3.  Définir le **icône par défaut** propriété d’un élément décoratif icône.  
  
2.  Sélectionnez le mappage d’élément de diagramme, qui est la ligne grise entre la classe de forme et de la classe de domaine sur le diagramme de définition DSL.  
  
3.  Dans la fenêtre Détails DSL, dans le **Decorator Maps** , sélectionnez un élément décoratif. Par exemple, le MaleDecorator.  
  
4.  Vérifiez le **filtre de visibilité** boîte.  
  
5.  Si la propriété de domaine qui doit-elle contrôler la visibilité est sur la classe de domaine immédiate, laissez **chemin d’accès à la propriété Filter** vide.  
  
     Sinon, cliquez sur le menu déroulant et accédez à la classe où se trouve la propriété ou de relation.  
  
    -   Pour éviter un rapport d’erreurs, vous ne devez pas naviguer via une relation marquée avec « * » dans l’outil de navigation.  
  
6.  Définir le **propriété Filter** à une propriété de domaine. Par exemple, le sexe.  
  
7.  Dans le **visibilité entrées** liste, ajouter des valeurs de cette propriété de domaine pour lequel le decorator doit être visible. Par exemple, homme.  
  
8.  Répétez les étapes pour chaque icône.  
  
9. **Transformer tous les modèles**, générer et exécuter et ouvrez un diagramme de test.  
  
10. Lorsque vous modifiez la valeur de propriété de contrôle, les éléments décoratifs doivent apparaissent et disparaissent.  
  
 Fréquemment, vous souhaitez que la visibilité d’être contrôlés par une formule plus complexe qu’un simple ensemble de valeurs. Par exemple, une icône dépend du nombre de liens d’un type particulier ou pour le rendre dépendent si un nombre est dans une plage particulière. Dans ce cas, utilisez la procédure suivante.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Pour contrôler la visibilité d’un élément décoratif basée sur une formule  
  
1.  Ajouter une propriété de domaine calculée à la classe de domaine. Dans le **propriétés** fenêtre, définissez les valeurs suivantes :  
  
     **IsBrowsable =**`False`**-cela masque la propriété à partir de l’utilisateur**   
  
     **Type =**`Calculated`**-cela signifie que vous fournissez le code qui calcule sa valeur**   
  
     **Nom** par exemple **DecoratorControl**  
  
     **Type** = `Boolean`  
  
     Pour plus d’informations, consultez [calculé et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Vérifiez la nouvelle propriété de contrôler la visibilité decorator.  
  
    1.  Sélectionnez le mappage d’élément de diagramme, qui est la ligne grise à partir de la classe de domaine à la forme. Dans le **détails DSL** fenêtre, ouvrez le **DecoratorMap** onglet.  
  
    2.  Vérifiez le **filtre de visibilité** boîte.  
  
    3.  Dans **propriété Filter**, sélectionnez la propriété du contrôle **DecoratorControl**.  
  
    4.  Sous **visibilité entrées**, entrez `True`.  
  
3.  Cliquez sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions.  
  
4.  Cliquez sur **générer la Solution** sur la **générer** menu.  
  
5.  Double-cliquez sur le rapport d’erreurs est apparu : «*YourClass* ne contient pas de définition pour GetDecoratorControlValue... ».  
  
     L’éditeur de texte s’ouvre sur Dsl\GeneratedCode\DomainClasses.cs. L’erreur en surbrillance est un commentaire qui vous permet d’ajouter une méthode de demande.  
  
6.  Notez l’espace de noms, classes et des méthodes qui sont manquants.  Par exemple, Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  Dans un fichier de code distinct, écrivez une définition de classe partielle qui contient la méthode manquante. Exemple :  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Pour plus d’informations sur la personnalisation du modèle avec le code de programme, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Régénérer et exécuter la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des formes et connecteurs](../modeling/defining-shapes-and-connectors.md)   
 [Définition d’une Image d’arrière-plan sur un diagramme](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)