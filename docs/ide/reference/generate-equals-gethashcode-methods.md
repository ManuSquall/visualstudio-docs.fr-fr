---
title: Générer des remplacements de méthode C# Equals et GetHashCode
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569281"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Générer des substitutions des méthodes Equals et GetHashCode dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** vous permet de générer les méthodes **Equals** et **GetHashCode**.

**Quand :** générez ces substitutions quand vous disposez d’un type qui doit être comparé selon un ou plusieurs champs et non selon l’emplacement de l’objet en mémoire.

**Pourquoi**

- si vous implémentez un type de valeur, vous pouvez substituer la méthode **Equals** afin d’améliorer les performances par rapport à l’implémentation par défaut de la méthode Equals sur ValueType.

- Si vous implémentez un type référence, vous devez envisager de substituer la méthode **Equals** si votre type ressemble à un type de base, tel que point, String, BigNumber, etc.

- Substituez la méthode **GetHashCode** pour permettre à un type de fonctionner correctement dans une table de hachage. Consultez la section sur les [opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procédures

1. Placez votre curseur quelque part sur la ligne de votre déclaration de type.

   ![Code mis en surbrillance](media/overrides-highlight-cs.png)

   > [!TIP]
   > N’effectuez pas de double-clic, sélectionnez le nom de type, sinon l’option de menu n’est pas disponible. Placez simplement le curseur quelque part sur la ligne.

1. Effectuez ensuite l'une des opérations suivantes :

   - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.

   - Cliquez sur l’icône ![Tournevis](../media/screwdriver-icon.png) qui apparaît dans la marge de gauche.

   ![Générer un aperçu des substitutions](media/overrides-preview-cs.png)

1. Sélectionnez **Générer Equals(object)** ou **Générer Equals et GetHashCode** dans le menu déroulant.

1. Dans la boîte de dialogue **Choisir les membres**, sélectionnez les membres pour lesquels vous souhaitez générer des méthodes :

    ![Boîte de dialogue Générer les substitutions](media/overrides-dialog-cs.png)

    > [!TIP]
    > Vous pouvez également choisir de générer des opérateurs à partir de cette boîte de dialogue en utilisant la case à cocher en bas de celle-ci.

   Les méthodes `Equals` et `GetHashCode` sont générées avec des implémentations par défaut.

   ![Résultat de l’action Générer une méthode](media/overrides-result-cs.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
