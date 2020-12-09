---
title: Modifier & Continuer (Visual Basic) | Microsoft Docs
description: Modifier & Continuer est disponible pour les projets Visual Basic. Découvrez les modifications qui sont prises en charge et comment contrôler si vos modifications sont appliquées et à quel moment.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4560973cd6ccd2bbfee48028494731935945a4c
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862969"
---
# <a name="edit-and-continue-visual-basic"></a>Modifier & Continuer (Visual Basic)
La fonctionnalité Modifier &amp; Continuer destinée au débogage de [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] vous permet d’apporter des modifications à votre code pendant qu’il s’exécute en mode Arrêt. Après avoir modifié le code, vous pouvez continuer son exécution avec les nouvelles modifications en place et observer leurs effets.

 Vous pouvez utiliser la fonctionnalité Modifier &amp; Continuer toutes les fois que vous passez en mode Arrêt. En mode arrêt, le pointeur d’instruction, une flèche jaune dans la fenêtre source, pointe vers la ligne contenant une instruction exécutable dans le corps d’une méthode ou d’une propriété qui sera exécutée ensuite.

 L'option Modifier &amp; Continuer prend en charge la plupart des modifications que vous pouvez souhaiter apporter pendant une session de débogage, avec quelques exceptions. Pour plus d’informations, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Lorsque vous procédez à une modification non autorisée, celle-ci est soulignée d’un trait ondulé violet et une tâche s’affiche dans la liste des tâches. Vous devez annuler une modification non autorisée si vous souhaitez continuer à utiliser Modifier &amp; Continuer. Certaines modifications non autorisées peuvent être permises si elles sont réalisées en dehors de Modifier &amp; Continuer. Si vous souhaitez conserver le résultat d'une modification non autorisée, vous devez arrêter le débogage et redémarrer votre application.

 Modifier & Continuer est pris en charge dans les applications UWP pour Windows 10, et les applications x86 et x64 qui ciblent le .NET Framework 4,6 ou les versions ultérieures (le .NET Framework est une version de bureau uniquement).

 > [!NOTE]
 > Les applications et les plateformes non prises en charge incluent ASP.NET 5, Silverlight 5 et Windows 8.1.

 Modifier etContinuer n'est pas pris en charge lorsque vous commencez à déboguer à l'aide d'**Attacher au processus**. Modifier & Continuer n’est pas pris en charge pour le code optimisé ou le code managé et natif mixte. Pour plus d’informations, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Les rubriques de cette section fournissent des détails supplémentaires sur l’utilisation de cette fonctionnalité et les types de modifications non autorisés.

## <a name="in-this-section"></a>Dans cette section
 [Comment : appliquer des modifications en mode arrêt avec modifier & continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Explique comment appliquer des modifications de code en mode arrêt.

 [Modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md) Décrit les types de modifications qui ne peuvent pas être effectuées dans [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] modifier & continuer.

## <a name="related-sections"></a>Sections connexes
 [Modifier & continuer](../debugger/edit-and-continue.md) Fournit une liste de rubriques sur Modifier & continuer.
