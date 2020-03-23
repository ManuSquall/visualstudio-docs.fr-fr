---
title: Refactoriser un champ en propriété
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: db0bd17cd0bead3807f857b2198b8d4ea4c72ffb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569710"
---
# <a name="encapsulate-a-field-refactoring"></a>Encapsuler un champ (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de transformer un champ en une propriété et de mettre à jour toutes les utilisations de ce champ afin d’utiliser cette nouvelle propriété.

**Quand :** vous souhaitez déplacer un champ vers une propriété et mettre à jour toutes les références à ce champ.

**Pourquoi :** vous voulez donner à d’autres classes l’accès à un champ, mais ne souhaitez pas que ces classes dispose d’un accès direct.  En encapsulant le champ dans une propriété, vous pouvez écrire un code pour vérifier la valeur assignée, par exemple.

## <a name="how-to"></a>Procédures

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à encapsuler :

   - C# :

       ![Code mis en surbrillance (C#)](media/encapsulate-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/encapsulate-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+E**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez l’entrée **Encapsuler le champ** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Encapsuler le champ**.
      - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez l’entrée **Encapsuler le champ** dans la fenêtre contextuelle d’aperçu.

   Sélection | Description
   --------- | -----------
   **Encapsuler le champ (et utiliser la propriété)** | Encapsule le champ avec une propriété et met à jour toutes les utilisations du champ afin d’utiliser la propriété générée
   **Encapsuler le champ (mais utiliser toujours le champ)** | Encapsule le champ avec une propriété, mais conserve intactes toutes les utilisations de ce champ

   La propriété est créée et les références au champ sont mises à jour, le cas échéant.

   > [!TIP]
   > Utilisez le lien **de modifications d’aperçu** dans la fenêtre popup [pour voir quel sera le résultat](../../ide/preview-changes.md) avant de s’y engager.

   - C# :

      ![Résultat de l’action Encapsuler une propriété (C#)](media/encapsulate-result-cs.png)

   - Visual Basic :

      ![Résultat de l’action Encapsuler une propriété (Visual Basic)](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
