---
title: Contrôle de la visibilité d'une icône ou d'un élément décoratif
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cfe6ce02b03ed69435f8056ccd340b92f9eb5a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421497"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Contrôle de la visibilité d'une icône ou d'un élément décoratif
Un *decorator* est une icône ou une ligne de texte qui apparaît sur la forme d’un langage spécifique à un domaine (DSL). Vous pouvez afficher l’élément décoratif et disparaissent selon l’état des propriétés dans le modèle. Par exemple, sur une forme représentant une personne, vous pouvez avoir des icônes différentes qui s’affichent en fonction du sexe de la personne, nombre d’enfants et ainsi de suite.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Contrôle de la visibilité d’une icône ou d’élément décoratif
 La procédure suivante suppose que vous avez déjà défini une forme et son mappage à une classe de domaine. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Pour contrôler la visibilité d’un élément décoratif icône ou du texte

1. Dans le diagramme de définition DSL, vous devez ajouter à la classe shape les icônes ou les éléments décoratifs de texte que vous souhaitez voir apparaître.

   1. Avec le bouton droit de la classe de forme, pointez sur **ajouter**, puis cliquez sur le type d’élément décoratif nécessaire.

   2. Valeur de l’élément décoratif **Position** propriété. Plusieurs éléments décoratifs peut avoir la même position. Par exemple, vous pourriez avoir des icônes pour homme et Femme partage la même position.

   3. Définir le **icône par défaut** propriété d’un élément décoratif d’icône.

2. Sélectionnez le mappage d’élément de diagramme, qui est la ligne grise entre la classe de forme et de la classe de domaine sur le diagramme de définition DSL.

3. Dans la fenêtre Détails DSL, dans le **mappages de décorateurs** , sélectionnez un élément décoratif. Par exemple, le MaleDecorator.

4. Vérifier le **filtre de visibilité** boîte.

5. Si la propriété de domaine qui doit-elle contrôler la visibilité est sur la classe de domaine immédiate, laissez **chemin d’accès à la propriété de filtre** vide.

    Sinon, cliquez sur le menu déroulant et accédez à la classe où se trouve la propriété ou de relation.

   - Pour éviter un rapport d’erreurs, vous ne devez pas naviguer via une relation marquée avec « * » dans l’outil de navigation.

6. Définir le **propriété Filter** à une propriété de domaine. Par exemple, le sexe.

7. Dans le **entrées de visibilité** liste, ajoutez les valeurs de cette propriété de domaine pour lequel l’élément décoratif doit être visible. Par exemple, homme.

8. Répétez les étapes pour chaque icône.

9. **Transformer tous les modèles**, générer et exécuter et ouvrez un diagramme de test.

10. Lorsque vous modifiez la valeur de propriété de contrôle, les éléments décoratifs doivent apparaître et disparaître.

    Fréquemment, vous souhaitez visibilité pour être contrôlé par une formule plus complexe qu’un simple ensemble de valeurs. Par exemple, une icône dépend du nombre de liens d’un type particulier, ou pour le rendre varient selon un qu’un nombre est dans une plage particulière. Dans ce cas, procédez comme suit.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Pour contrôler la visibilité d’un décorateur selon une formule

1. Ajouter une propriété de domaine calculée à la classe de domaine. Dans le **propriétés** fenêtre, définissez les valeurs suivantes :

     **IsBrowsable =**`False`**-cela masque la propriété à partir de l’utilisateur**

     **Type =**`Calculated`**-cela signifie que vous fournirez code qui calcule sa valeur**

     **Nom** par exemple **DecoratorControl**

     **Type** = `Boolean`

     Pour plus d’informations, consultez [calculées et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).

2. Vérifiez la nouvelle propriété de contrôler la visibilité de décorateur.

    1. Sélectionnez le mappage d’élément de diagramme, qui est la ligne grise à partir de la classe de domaine à la forme. Dans le **détails DSL** fenêtre, ouvrez le **DecoratorMap** onglet.

    2. Vérifier le **filtre de visibilité** boîte.

    3. Dans **propriété Filter**, sélectionnez la propriété du contrôle **DecoratorControl**.

    4. Sous **entrées de visibilité**, entrez `True`.

3. Cliquez sur **transformer tous les modèles** dans le **l’Explorateur de solutions** barre d’outils.

4. Cliquez sur **générer la Solution** sur le **Build** menu.

5. Double-cliquez sur le rapport d’erreurs qui s’est affiché : «*Votre_classe* ne contient pas de définition pour GetDecoratorControlValue... ».

     L’éditeur de texte s’ouvre sur Dsl\GeneratedCode\DomainClasses.cs. Au-dessus de l’erreur en surbrillance est un commentaire que vous êtes invité à ajouter une méthode.

6. Notez l’espace de noms, classe et méthode qui sont manquants.  Par exemple, Company.FamilyTree.Person.GetDecoratorControlValue().

7. Dans un fichier de code séparé, écrivez une définition de classe partielle qui contient la méthode manquante. Exemple :

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Pour plus d’informations sur la personnalisation du modèle avec le code de programme, consultez [navigation et la mise à jour un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Régénérez et exécutez la solution.

## <a name="see-also"></a>Voir aussi

- [Définition de formes et de connecteurs](../modeling/defining-shapes-and-connectors.md)
- [Définition d’une image d’arrière-plan dans un diagramme](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)