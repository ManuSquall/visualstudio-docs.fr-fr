---
title: Débogage d’applications Mixed-Mode | Microsoft Docs
description: Déboguez une application en mode mixte, qui est une application qui combine du code natif avec du code managé qui s’exécute sur le common language runtime, dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eff1cae9c1895e853712218d5e0ae55e3138c41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872610"
---
# <a name="debugging-mixed-mode-applications"></a>Débogage des applications en mode mixte
Une application en mode mixte est une application qui combine du code natif (C++) avec du code managé (tel que Visual Basic, Visual C# ou C++ qui s'exécute sur le Common Language Runtime). Le débogage d'applications en mode mixte est largement transparent dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il n'est pas très différent du débogage d'une application en mode unique. Quelques considérations spéciales sont toutefois à prendre en compte.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Permettre l'opération Modifier &amp; Continuer pour C++ dans le cadre du débogage en mode mixte

Pour activer modifier & Continuer pour C++, consultez [Comment activer et désactiver modifier & continuer](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Pour pouvoir utiliser l'opération Modifier &amp; Continuer pour C++ dans Visual Studio 2013, vous devez revenir au moteur de débogage hérité. Consultez [Switching to Managed Compatibility Mode in Visual Studio 2013](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) dans le blog relatif à la gestion du cycle de vie des applications Microsoft.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Évaluation de propriété dans les applications en mode mixte
 Dans une application en mode mixte, l'évaluation des propriétés par le débogueur est une opération coûteuse. Par conséquent, le débogage d'opérations telles que l'exécution pas à pas peut sembler lent. Pour plus d’informations, consultez [Exécution pas à pas](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Si vos performances sont faibles lors du débogage en mode mixte, vous pouvez désactiver l'évaluation de propriété dans les fenêtres du débogueur.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Pour désactiver l'évaluation de propriété

1. Dans le menu **Outils**, choisissez **Options**.

2. Dans la boîte de dialogue **Options**, ouvrez le dossier **Débogage** et sélectionnez la catégorie **Général**.

3. Décochez la case **Activer l’évaluation de la propriété et d’autres appels de fonction implicite**.

   Dans la mesure où les piles des appels natives et managées sont différentes, le débogueur ne peut pas toujours fournir la pile des appels complète pour le code mixte. Lorsque le code natif appelle le code managé, il est possible que vous notiez certaines divergences. Pour plus d’informations, consultez [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>Voir aussi

- [Débogage du code managé](../debugger/debugging-managed-code.md)