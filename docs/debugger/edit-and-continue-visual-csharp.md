---
title: Modifier & Continuer (Visual C#) | Microsoft Docs
description: Modifier & Continuer est disponible pour les projets Visual C#. Découvrez les modifications qui sont prises en charge et comment contrôler si vos modifications sont appliquées et à quel moment.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 375e1db598f925a193def159203ccb7e5c5fdf05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871856"
---
# <a name="edit-and-continue-visual-c"></a>Modifier & Continuer (Visual C#)
 Avec Modifier &amp; Continuer pour C#, vous pouvez modifier votre code en mode arrêt pendant le débogage. Les modifications peuvent être appliquées sans qu'il soit nécessaire d'arrêter et de redémarrer la session de débogage. En mode exécution, l'éditeur de code source est en lecture seule.

 L'option Modifier &amp; Continuer prend en charge la plupart des modifications que vous pouvez souhaiter apporter pendant une session de débogage, avec quelques exceptions. Pour plus d’informations, consultez [modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Modifier & Continuer est pris en charge dans UWP dans Windows 10, et les applications x86 et x64 qui ciblent le .NET Framework 4,6 ou les versions ultérieures (le .NET Framework est une version de bureau uniquement).

 > [!NOTE]
 > Les applications et plateformes non prises en charge incluent Silverlight 5 et Windows 8.1.

 Quand l’option Modifier & Continuer est activée, les modifications prises en charge sont appliquées automatiquement lorsque vous utilisez une commande d’exécution du débogueur, par exemple **Continuer**, **Exécuter pas à pas** ou **Définir l’instruction suivante**, ou lorsque vous exécutez une évaluation de fonction dans une fenêtre du débogueur.

 Pour plus d’informations, consultez [Comment : utiliser modifier & continuer (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour utiliser Modifier & Continuer (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Modifications de code prises en charge (C# et Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML dans Visual Studio](../xaml-tools/xaml-hot-reload.md)
