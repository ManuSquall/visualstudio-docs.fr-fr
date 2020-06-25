---
title: Comment-déboguer en mode mixte | Microsoft Docs
ms.date: 11/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53a40c4dc615b5e1b6a3caef3a99be5ab0b56327
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350106"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Comment : déboguer en mode mixte (C#, C++, Visual Basic)

Les procédures suivantes décrivent comment activer conjointement le débogage pour le code managé et le code natif, également appelé débogage en mode mixte. Il existe deux scénarios de débogage en mode mixte :

- L’application qui appelle une DLL est écrite en code natif, et la DLL est gérée.

- L’application qui appelle une DLL est écrite en code managé, et la DLL est en code natif. Pour obtenir un didacticiel qui vous guide dans ce scénario plus en détail, consultez [déboguer le code managé et natif](../debugger/how-to-debug-managed-and-native-code.md).

Vous pouvez activer les débogueurs managés et natifs dans les pages de **Propriétés** du projet d’application appelant. Les paramètres varient selon les applications natives et gérées.

Si vous n’avez pas accès au projet d’une application appelante, vous pouvez déboguer la DLL à partir du projet DLL. Vous n’avez pas besoin du mode mixte pour déboguer uniquement le projet DLL. Pour plus d’informations, consultez [Comment : déboguer à partir d’un projet dll](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Les boîtes de dialogue et les commandes qui s’affichent peuvent être différentes de celles de cet article, en fonction de vos paramètres ou de votre édition de Visual Studio. Pour modifier vos paramètres, choisissez **Outils**  >  **importation et exportation de paramètres**. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Activer le débogage en mode mixte pour une application appelante Native

1. Sélectionnez le projet C++ dans **Explorateur de solutions** puis cliquez sur l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Dans la boîte de dialogue ** \<Project> pages de propriétés** , développez **Propriétés de configuration**, puis sélectionnez **débogage**.

1. Définissez **Type de débogueur** sur **Mixte** ou **Automatique**.

1. Sélectionnez **OK**.

   ![Activer le débogage en mode mixte](../debugger/media/dbg-mixed-mode-from-native.png "Activer le débogage en mode mixte")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Activer le débogage en mode mixte pour une application appelante managée

1. Sélectionnez le projet C# ou Visual Basic dans **Explorateur de solutions** et sélectionnez l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Sélectionnez l’onglet **Déboguer** , puis sélectionnez **activer le débogage du code natif**.

1. Fermez la page des propriétés pour enregistrer les modifications.

   ![Activer le débogage du code natif](../debugger/media/dbg-mixed-mode-from-csharp.png "Activer le débogage du code natif")

> [!NOTE]
> Dans la plupart des versions de Visual Studio à compter de Visual Studio 2017, vous devez utiliser le fichier *launchSettings.json* au lieu des propriétés du projet pour activer le débogage en mode mixte pour le code natif dans une application .NET Core. Pour plus d’informations, consultez [déboguer le code managé et natif](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour déboguer à partir d’un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)