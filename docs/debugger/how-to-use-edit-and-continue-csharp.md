---
title: Utiliser modifier & Continuer (C#) | Microsoft Docs
description: Utilisez modifier & Continuer pour apporter et appliquer les modifications à votre code en mode arrêt pendant le débogage, sans arrêter et redémarrer la session de débogage dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ed538c49aeb1257b165d7cfecab0352dd0deb488
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889172"
---
# <a name="how-to-use-edit-and-continue-c"></a>Comment : utiliser Modifier &amp; Continuer (C#)
Avec modifier & continuer, vous pouvez apporter et appliquer des modifications à votre code en mode arrêt pendant le débogage, sans avoir à arrêter et redémarrer la session de débogage.

Modifier & Continuer pour C# se produit automatiquement lorsque vous apportez des modifications de code en mode arrêt, puis continuez le débogage à l’aide de l’instruction **continue**, **Step** ou **Set Next**, ou évaluez une fonction dans une fenêtre du débogueur.

Pour plus d’informations, consultez [modifier & continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Modifier & Continuer n’est pas pris en charge pour le code d’intégration optimisé, mixte ou SQL Server common language runtime (CLR). Pour plus d’informations sur les autres scénarios non pris en charge, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md). Si vous essayez de modifier et de continuer avec l’un de ces scénarios, une boîte de message s’affiche indiquant que modifier & Continuer n’est pas pris en charge.

**Pour activer ou désactiver modifier & Continuer :**

1. Si vous êtes dans une session de débogage, arrêtez le débogage (**Déboguer**  >  **arrêter le débogage** ou **MAJ** + **F5**).

1. Dans   >  **options** des outils (ou options de **débogage**  >  ) > **débogage**  >  **général**, activez ou désactivez la case à cocher **activer modifier et continuer** .

Le paramètre prend effet lorsque vous démarrez ou redémarrez la session de débogage.

**Pour utiliser modifier & Continuer :**

1. Lors du débogage, en mode arrêt, apportez une modification à votre code source.

1. Dans le menu **Déboguer** , cliquez sur **Continuer**, **exécuter pas à pas** ou **définir l’instruction suivante**, ou évaluer une fonction dans une fenêtre du débogueur.

   Le débogage se poursuit avec le nouveau code compilé.

Certains types de modifications du code ne sont pas pris en charge par modifier & continuer. Pour plus d’informations, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).
