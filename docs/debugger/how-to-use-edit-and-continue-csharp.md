---
title: 'Comment : utiliser Modifier & Continuer (C#) | Microsoft Docs'
ms.date: 10/04/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 515068f29045ef92ee7d2323f752ba2185f28cac
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696348"
---
# <a name="how-to-use-edit-and-continue-c"></a>Comment : utiliser Modifier &amp; Continuer (C#)
Avec Modifier & Continuer, vous pouvez apporter et appliquer des modifications à votre code en mode arrêt pendant le débogage, sans avoir à arrêter et redémarrer la session de débogage.

Modifier & Continuer pour C# se produit automatiquement lorsque vous apportez des modifications de code en mode arrêt, puis continuez le débogage à l’aide de **continuer**, **étape**, ou **définir l’instruction suivante**, ou évaluez une fonction dans une fenêtre du débogueur.

Pour plus d’informations, consultez [Modifier & Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Modifier & Continuer n’est pas pris en charge pour optimisé, mixte, ou code de l’intégration SQL Server common language runtime (CLR). Pour plus d’informations sur les autres scénarios non pris en charge, consultez [pris en charge les modifications de code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md). Si vous tentez de modifier & Continuer avec l’un de ces scénarios, une boîte de message s’affiche indiquant que Modifier & Continuer n’est pas compatible.

**Pour activer ou désactiver Modifier & Continuer :**

1. Si vous êtes dans une session de débogage, arrêtez le débogage (**déboguer** > **arrêter le débogage** ou **MAJ**+**F5**) .

1. Dans **outils** > **Options** (ou **déboguer** > **Options**) > **dedébogage**  >  **Général**, activez ou désactivez le **Activer Modifier & Continuer** case à cocher.

Le paramètre prend effet lorsque vous démarrez ou redémarrez la session de débogage.

**Pour utiliser Modifier & Continuer :**

1. Pendant le débogage, en mode arrêt, apportez une modification à votre code source.

1. À partir de la **déboguer** menu, cliquez sur **continuer**, **étape**, ou **définir l’instruction suivante**, ou évaluez une fonction dans une fenêtre du débogueur.

   Débogage de se poursuit avec le nouveau code compilé.

Certains types de modifications du code ne sont pas pris en charge par Modifier & Continuer. Pour plus d’informations, consultez [pris en charge les modifications de code (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).
