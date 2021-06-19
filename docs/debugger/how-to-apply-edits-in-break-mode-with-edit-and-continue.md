---
title: Appliquer les modifications en mode arrêt avec modifier & continuer | Microsoft Docs
description: Consultez Comment utiliser modifier & Continuer pour modifier votre code Visual Basic en mode arrêt. Il existe plusieurs façons de passer en mode arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e62c6a7a6e30bac6d054f3e5484498047426d96d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386798"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Comment : appliquer des modifications en mode arrêt à l’aide de la fonction Modifier & Continuer (Visual Basic)
Vous pouvez utiliser Modifier &amp; Continuer pour modifier votre code en mode Arrêt, puis continuer sans arrêter et redémarrer l'exécution.

Pour connaître les limitations relatives à l’utilisation de modifier & continuer pendant le débogage, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Pour modifier du code en mode Arrêt

1. Passez en mode Arrêt en procédant de l'une des manières suivantes :

    - Définissez un point d’arrêt dans votre code, puis cliquez sur **Démarrer le débogage** dans le menu **Déboguer** et attendez que l’application parvienne au point d’arrêt.

         -ou-

    - Démarrez le débogage, puis sélectionnez **Interrompre tout** dans le menu **Déboguer**.

         -ou-

    - Quand une exception se produit, choisissez **activer la modification** dans l' **Assistant Exception**.

2. Apportez les modifications de code souhaitées et prises en charge.

     Pour plus d’informations, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Si vous tentez d'effectuer une modification du code qui n'est pas autorisée par l'opération Modifier &amp; Continuer, votre modification est soulignée d'un trait ondulé violet et une tâche s'affiche dans la liste des tâches. Il vous est impossible de continuer l'exécution du code sauf si vous annulez la modification de code non autorisée.

3. Dans le menu **Déboguer**, cliquez sur **Continuer** pour reprendre l’exécution.

     Votre code s'exécute désormais avec les modifications que vous avez appliquées dans le projet.

## <a name="see-also"></a>Voir aussi
- [Modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Modifier &amp; Continuer (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
