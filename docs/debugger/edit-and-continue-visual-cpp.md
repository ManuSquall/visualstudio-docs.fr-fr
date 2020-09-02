---
title: Modifier & Continuer (C++) | Microsoft Docs
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c2d92477e37b4918e0601bf163e07f5a8492136c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72737896"
---
# <a name="edit-and-continue-c"></a>Modifier & Continuer (C++)
Vous pouvez utiliser modifier & continuer dans les projets C++. Pour plus d’informations sur les limitations de modifier & continuer, consultez [modifications de code prises en charge (C++)](../debugger/supported-code-changes-cpp.md) .

Pour plus d’informations sur les améliorations de Visual Studio 2015 Update 3, consultez [modifier & continuer dans Visual studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 L’option de compilateur [/Zo (Améliorer le débogage optimisé)](/cpp/build/reference/zo-enhance-optimized-debugging) qui a été introduite dans Visual Studio 2013 Update 3 ajoute des informations aux fichiers de symboles (.pdb) pour les fichiers binaires compilés sans l’option [/Od (Désactiver (Débogage))](https://msdn.microsoft.com/library/aafb762y.aspx).

 **/Zo** désactive modifier & continuer. Consultez [Guide pratique pour déboguer le code optimisé](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Activer ou désactiver Modifier & Continuer
 Vous pouvez désactiver l’appel automatique de Modifier & Continuer si vous apportez des modifications au code que vous ne souhaitez pas appliquer tout de suite, pendant la session de débogage en cours. Vous pouvez également réactiver la fonctionnalité automatique Modifier & Continuer.

> [!IMPORTANT]
> Pour obtenir les paramètres de build requis et d’autres informations sur la compatibilité des fonctionnalités, consultez [modifier & continuer dans Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Si vous êtes dans une session de débogage, arrêtez le débogage (**Maj + F5**).

2. Dans le menu **Outils**, choisissez **Options**.

3. Dans la boîte de dialogue **options** , sélectionnez **débogage > général**.

4. Pour activer, sélectionnez **activer modifier & continuer**. Pour désactiver, désactivez la case à cocher.

5. Dans le groupe **Modifier &amp; Continuer** , cochez ou décochez la case **Activer Modifier et Continuer natif** .

   La modification de ce paramètre s’applique à tous vos projets actuels. Après avoir modifié ce paramètre, il n'est pas nécessaire de régénérer l'application. Si vous générez votre application à partir de la ligne de commande ou d’un Makefile, mais que vous effectuez le débogage dans l’environnement Visual Studio, vous pouvez toujours utiliser modifier & continuer si vous définissez l’option **/Zi** .

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Comment appliquer des modifications du code explicitement
 En C++, modifier & continuer peut appliquer des modifications de code de deux manières. Les modifications du code peuvent être implicitement appliquées, lorsque vous choisissez une commande d'exécution, ou explicitement, à l'aide de la commande **Appliquer les modifications du code** .

 Quand vous appliquez des modifications du code de manière explicite, votre programme reste en mode arrêt - aucune exécution ne se produit.

- Pour appliquer les modifications du code explicitement, dans le menu **Déboguer** , choisissez **Appliquer les modifications du code**.

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Comment arrêter des modifications de code
 Pendant que Modifier & Continuer est en train d'appliquer les modifications du code, vous pouvez arrêter l'opération.

 Pour arrêter d'appliquer les modifications du code :

- Dans le menu **Déboguer** , choisissez **Cesser d'appliquer les modifications du code**.

  Cet élément de menu est visible uniquement lorsque les modifications du code sont appliquées.

  Si vous choisissez cette option, aucune modification du code n'est validée.

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Comment réinitialiser le point d'exécution
 Certaines modifications du code peuvent entraîner le déplacement du point d'exécution vers un nouvel emplacement lorsque le mode Modifier & Continuer applique les modifications. Bien que Modifier & Continuer place le point d'exécution aussi précisément que possible, les résultats risquent d'être incorrects dans certains cas.

 En C++, une boîte de dialogue vous informe lorsque le point d’exécution change. Vérifiez que le nouvel emplacement est correct avant de poursuivre le débogage. S'il ne l'est pas, utilisez la commande **Définir l'instruction suivante** . Pour plus d’informations, consultez [Définir l’instruction suivante à exécuter](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Comment utiliser du code périmé
 Dans certains cas, Modifier & Continuer n'applique pas immédiatement les modifications du code au fichier exécutable, mais peut éventuellement les appliquer ultérieurement si vous poursuivez le débogage. Cela arrive si vous modifiez une fonction qui appelle la fonction actuelle ou si vous ajoutez plus de 64 octets de nouvelles variables à une fonction sur la pile des appels.

 Dans ces cas, le débogueur continue à exécuter le code d’origine jusqu’à ce que les modifications puissent être appliquées. Le code périmé apparaît comme une fenêtre de fichier source temporaire dans une fenêtre source séparée, avec un titre comme `enc25.tmp`. La source modifiée continue à apparaître dans la fenêtre source d'origine. Si vous essayez de modifier le code périmé, un message d'avertissement apparaît.

## <a name="see-also"></a>Voir aussi
- [Modifications du code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)