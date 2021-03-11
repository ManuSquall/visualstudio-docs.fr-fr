---
title: Générer des remplacements de méthode C# Equals et GetHashCode
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour générer des méthodes Equals et GetHashCode.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 597d17b69aa3f0feca520e6100439d934e5d9211
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607338"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Générer des substitutions des méthodes Equals et GetHashCode dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** vous permet de générer les méthodes **Equals** et **GetHashCode**.

**Quand :** générez ces substitutions quand vous disposez d’un type qui doit être comparé selon un ou plusieurs champs et non selon l’emplacement de l’objet en mémoire.

**Pourquoi**

- Si vous implémentez un type de valeur, vous devez envisager de substituer la méthode **Equals** . Vous pouvez améliorer les performances par rapport à l’implémentation par défaut de la méthode Equals sur ValueType lorsque vous procédez ainsi.

- Si vous implémentez un type référence, vous devez envisager de substituer la méthode **Equals** si votre type ressemble à un type de base, tel que point, String, BigNumber, etc.

- Substituez la méthode **GetHashCode** pour permettre à un type de fonctionner correctement dans une table de hachage. Consultez la section sur les [opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procédures

1. Placez votre curseur quelque part sur la ligne de votre déclaration de type.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   Votre code doit ressembler à la capture d’écran suivante :

   ![Capture d’écran du code mis en surbrillance sur lequel appliquer la méthode générée](media/overrides-highlight-cs.png)

   > [!TIP]
   > N’effectuez pas de double-clic, sélectionnez le nom de type, sinon l’option de menu n’est pas disponible. Placez simplement le curseur quelque part sur la ligne.

1. Ensuite, choisissez l’une des actions suivantes :

   - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.

   - Cliquez sur le bouton ![Capture d’écran de l’icône du tournevis actions rapides dans Visual Studio](../media/screwdriver-icon.png) qui apparaît dans la marge de gauche.

1. Dans le menu déroulant, sélectionnez **générer Equals (Object)** ou **générer Equals et GetHashCode**.

   ![Capture d’écran du menu déroulant générer des remplacements](media/overrides-preview-cs.png)

1. Dans la boîte de dialogue **Choisir les membres**, sélectionnez les membres pour lesquels vous souhaitez générer des méthodes :

    ![Boîte de dialogue Générer les substitutions](media/overrides-dialog-cs.png)

    > [!TIP]
    > Vous pouvez également choisir de générer des opérateurs à partir de cette boîte de dialogue en utilisant la case à cocher en bas de celle-ci.

   Les `Equals` `GetHashCode` méthodes et sont générées avec les implémentations par défaut, comme illustré dans le code suivant :

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   Votre code doit ressembler à la capture d’écran suivante :

   ![Capture d’écran du résultat de la méthode générée](media/overrides-result-cs.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
