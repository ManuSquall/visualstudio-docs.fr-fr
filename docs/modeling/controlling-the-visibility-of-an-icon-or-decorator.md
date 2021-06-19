---
title: Contrôle de la visibilité d'une icône ou d'un élément décoratif
description: Découvrez comment vous pouvez contrôler la visibilité d’une icône ou d’un Decorator en fonction de l’état des propriétés dans le modèle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c60d66188364ddd18be1d60a92b51ee5d7a9fc8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389616"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Contrôle de la visibilité d'une icône ou d'un élément décoratif
Un élément *décoratif* est une icône ou une ligne de texte qui apparaît sur une forme dans un langage spécifique à un domaine (DSL). Vous pouvez faire en sorte que l’élément décoratif apparaisse et disparaisse en fonction de l’état des propriétés dans le modèle. Par exemple, sur une forme représentant une personne, vous pouvez avoir différentes icônes qui s’affichent en fonction du sexe, du nombre d’enfants, etc. de la personne.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Contrôle de la visibilité d’une icône ou d’un décorateur
 La procédure suivante suppose que vous avez déjà défini une forme et son mappage à une classe de domaine. Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Pour contrôler la visibilité d’une icône ou d’un élément décoratif de texte

1. Dans le diagramme de définition DSL, ajoutez à la classe Shape les icônes ou les éléments décoratifs de texte que vous souhaitez afficher.

   1. Cliquez avec le bouton droit sur la classe de forme, pointez sur **Ajouter**, puis cliquez sur le type d’élément décoratif requis.

   2. Définissez la propriété **position** de l’élément décoratif. Plusieurs Decorator peuvent avoir la même position. Par exemple, vous pouvez avoir des icônes pour les hommes et les femmes partageant la même position.

   3. Définissez la propriété **icône par défaut** d’un élément décoratif d’icône.

2. Sélectionnez le mappage d’élément de diagramme, qui est la ligne grise entre la classe de forme et la classe de domaine dans le diagramme de définition DSL.

3. Dans la fenêtre Détails DSL, sous l’onglet **mappages de décorateurs** , sélectionnez un Decorator. Par exemple, MaleDecorator.

4. Cochez la case **filtre de visibilité** .

5. Si la propriété de domaine qui doit contrôler la visibilité se trouve sur la classe de domaine immédiate, laissez la **propriété chemin d’accès au filtre** vide.

    Sinon, cliquez sur le menu déroulant et accédez à la relation ou à la classe où se trouve la propriété.

   - Pour éviter un rapport d’erreurs, vous ne devez pas naviguer dans une relation marquée avec « * » dans l’outil de navigation.

6. Définissez la **propriété de filtre** sur une propriété de domaine. Par exemple, sexe.

7. Dans la liste **entrées de visibilité** , ajoutez les valeurs de cette propriété de domaine pour lesquelles l’élément décoratif doit être visible. Par exemple, masculin.

8. Répétez les étapes pour chaque icône.

9. **Transformez tous les modèles**, générez et exécutez, puis ouvrez un diagramme de test.

10. Lorsque vous modifiez la valeur de la propriété de contrôle, les décorateurs doivent apparaître et disparaître.

    Souvent, vous souhaitez que la visibilité soit contrôlée par une formule plus complexe qu’un simple ensemble de valeurs. Par exemple, pour qu’une icône dépende du nombre de liens d’un type particulier, ou pour faire en sorte qu’elle dépende d’un nombre situé dans une plage particulière. Dans ce cas, utilisez la procédure suivante.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Pour contrôler la visibilité d’un élément décoratif en fonction d’une formule

1. Ajoutez une propriété de domaine calculé à la classe de domaine. Dans la fenêtre **Propriétés** , définissez les valeurs suivantes :

     **IsBrowsable =** `False` **: masque la propriété de l’utilisateur**    

     **Genre =** `Calculated` **-cela signifie que vous allez fournir le code qui calcule sa valeur**    

     **Nom** de l’exemple **DecoratorControl**

     **Entrer** = `Boolean`

     Pour plus d’informations, consultez [Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md).

2. Faites en sorte que la nouvelle propriété contrôle la visibilité de l’élément décoratif.

    1. Sélectionnez le mappage d’élément de diagramme, qui est la ligne grise entre la classe de domaine et la forme. Dans la fenêtre **Détails DSL** , ouvrez l’onglet **DecoratorMap** .

    2. Cochez la case **filtre de visibilité** .

    3. Dans **propriété de filtre**, sélectionnez la propriété de contrôle **DecoratorControl**.

    4. Sous **entrées de visibilité**, entrez `True` .

3. Cliquez sur **transformer tous les modèles** dans la barre d’outils **Explorateur de solutions** .

4. Dans le menu **générer** , cliquez sur **générer la solution** .

5. Double-cliquez sur le rapport d’erreurs qui s’est affiché : «*YourClass* ne contient pas de définition pour GetDecoratorControlValue... ».

     L’éditeur de texte s’ouvre sur Dsl\GeneratedCode\DomainClasses.cs. Au-dessus de l’erreur en surbrillance figure un commentaire qui vous demande d’ajouter une méthode.

6. Notez l’espace de noms, la classe et la méthode qui sont manquants.  Par exemple, société. FamilyTree. Person. GetDecoratorControlValue ().

7. Dans un fichier de code séparé, écrivez une définition de classe partielle qui contient la méthode manquante. Exemple :

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Pour plus d’informations sur la personnalisation du modèle à l’aide du code de programme, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Régénérez et exécutez la solution.

## <a name="see-also"></a>Voir aussi

- [Définition de formes et de connecteurs](../modeling/defining-shapes-and-connectors.md)
- [Définition d’une image d’arrière-plan dans un diagramme](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)