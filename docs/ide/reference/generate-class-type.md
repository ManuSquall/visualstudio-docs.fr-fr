---
title: Générer une classe ou un type
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595629"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Générer une classe ou un type dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement le code pour une classe ou un type.

**Quand :** vous introduisez une nouvelle classe ou un nouveau type et souhaitez les déclarer correctement, automatiquement.

**Pourquoi :** vous pouvez déclarer la classe ou le type avant de l’utiliser, mais cette fonctionnalité générera automatiquement la classe ou le type.

## <a name="how-to"></a>Procédures

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique une classe qui n’existe pas encore.

   - C# :

       ![Code C# mis en surbrillance](media/class-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/class-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît.
      - Cliquez sur le bouton ![ampoule d’erreur](media/error-bulb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

      ![Aperçu de l’action Générer la classe](media/class-preview-cs.png)

3. Sélectionnez l’une des options dans le menu déroulant :

   - Générer la classe '*TypeName*' dans un nouveau fichier&mdash;Crée une classe nommée *TypeName* dans un fichier nommé *TypeName*.cs/.vb.
   - Générer la classe '&mdash;*TypeName*' Crée une classe nommée *TypeName* dans le fichier actuel.
   - Générer classe imbriquée&mdash;'*TypeName*' Crée une classe nommée *TypeName* niché à l’intérieur de la classe actuelle.
   - Générer un nouveau type...&mdash;Crée une classe ou un struct avec toutes les propriétés que vous spécifiez.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

4. Si vous avez sélectionné l’élément **Générer un nouveau type**, la boîte de dialogue **Générer le type** s’ouvre. Configurez l’accessibilité, le genre et l’emplacement du nouveau type.

   ![Générer le type](media/class-newtype-cs.png)

   Sélection | Description
   --- | ---
   Accès | Définissez un accès *Par défaut*, *Interne* ou *Public* pour le type.
   Type | Peut être défini sur *classe* ou *structure*.
   Nom | Ce paramètre ne peut pas être modifié et affichera le nom que vous avez déjà tapé.
   Projet | Si votre solution contient plusieurs projets, vous pouvez choisir l’emplacement souhaité pour la classe/structure à utiliser.
   Nom de fichier | Vous pouvez créer un nouveau fichier, ou ajouter le type à un fichier existant.

La classe ou le struct est créé. Pour C#, un constructeur est également créé.

- C#

   ![Résultat de l’action Générer la classe (C#)](media/class-result-cs.png)

- Visual Basic

   ![Résultat de l’action Générer la classe (Visual Basic)](media/class-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Génération de codes](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
