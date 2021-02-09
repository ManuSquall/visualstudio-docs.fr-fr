---
title: Déboguer au moment du design | Microsoft Docs
description: Utilisez la fenêtre exécution pour déboguer le code au moment du design, sans exécuter l’application. Vous pouvez exécuter une fonction et examiner l’État lorsqu’un point d’arrêt est atteint.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2701542921bae4bb878bc48a3e16eda14416cdf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884102"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Débogage au moment du design dans Visual Studio (C#, C++/CLI, Visual Basic, F #)

Pour déboguer du code au moment du design plutôt que pendant qu’une application est en cours d’exécution, vous pouvez utiliser la fenêtre **exécution** .

Pour déboguer du code XAML derrière une application à partir du concepteur XAML, tel que des scénarios de liaison de données déclaratifs, vous pouvez utiliser l’attachement de **débogage**  >  **au processus**.

## <a name="use-the-immediate-window"></a>Utiliser la fenêtre exécution

Vous pouvez utiliser la fenêtre **exécution** Visual Studio pour exécuter une fonction ou une sous-routine sans exécuter votre application. Si la fonction ou la sous-routine contient un point d’arrêt, Visual Studio s’arrête au point d’arrêt. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée *débogage au moment de la conception*.

L’exemple suivant se trouve dans Visual Basic. Vous pouvez également utiliser la fenêtre **exécution** au moment du design dans des applications C#, F # et C++/CLI.

1. Collez le code suivant dans une application console Visual Basic vide :

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Définissez un point d’arrêt sur la **fonction line end**.

1. Ouvrez la fenêtre **exécution** en sélectionnant **Déboguer** les  >  **fenêtres**  >  **immédiates**. Tapez `?MyFunction` dans la fenêtre, puis appuyez sur **entrée**.

   Le point d’arrêt est atteint et la valeur de **MyFunction** dans la fenêtre **variables locales** est **1**. Vous pouvez examiner la pile des appels et les autres fenêtres de débogage pendant que l’application est en mode arrêt.

1. Sélectionnez **Continuer** dans la barre d’outils de Visual Studio. L’application se termine et **1** est retournée dans la fenêtre **exécution** . Assurez-vous que vous êtes toujours en mode création.

1. Tapez à `?MyFunction` nouveau dans la fenêtre **exécution** , puis appuyez sur **entrée**. Le point d’arrêt est atteint et la valeur de **MyFunction** dans la fenêtre **variables locales** est **2**.

1. Sans sélectionner **Continuer**, tapez `?MySub()` dans la fenêtre **exécution** , puis appuyez sur **entrée**. Le point d’arrêt est atteint et la valeur de **MyFunction** dans la fenêtre **variables locales** est **3**. Vous pouvez examiner l’état de l’application pendant que l’application est en mode arrêt.

1. Sélectionnez **Continuer**. Le point d’arrêt est à nouveau atteint et la valeur de **MyFunction** dans la fenêtre **variables locales** est maintenant **2**. La fenêtre **exécution** retourne l' **expression a été évaluée et n’a pas de valeur**.

1. Sélectionnez **Continuer** . L’application se termine et **2** est retournée dans la fenêtre **exécution** . Assurez-vous que vous êtes toujours en mode création.

1. Pour effacer le contenu de la fenêtre **exécution** , cliquez avec le bouton droit dans la fenêtre et sélectionnez **Effacer tout**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Déboguer un contrôle XAML personnalisé au moment du design en l’attachant au concepteur XAML

1. Ouvrez votre solution ou projet dans Visual Studio.

1. Générez la solution ou le projet.

1. Ouvrez la page XAML contenant le contrôle personnalisé que vous souhaitez déboguer.

   Pour les projets UWP ciblant Windows Build 16299 ou version ultérieure, cette étape permet de démarrer le processus de *UwpSurface.exe* . Pour les projets WPF ciblant Windows Build 16299 ou version ultérieure, cette étape permet de démarrer le processus de *WpfSurface.exe* . Pour les versions WPF ou UWP antérieures à la version 16299 de Windows, cette étape permet de démarrer le processus de *XDesProc.exe* . 

1. Ouvrez une deuxième instance de Visual Studio. N’ouvrez pas une solution ou un projet dans la deuxième instance.

1. Dans la deuxième instance de Visual Studio, ouvrez le menu **Déboguer** , puis choisissez **attacher au processus...**.

1. Selon le type de projet (voir les étapes précédentes), sélectionnez le *UwpSurface.exe*, *WpfSurface.exe* ou le processus *XDesProc.exe* dans la liste des processus disponibles.

1. Dans le champ **attacher à** de la boîte de dialogue **attacher au processus** , choisissez le type de code approprié pour le contrôle personnalisé que vous souhaitez déboguer.

   Si votre contrôle personnalisé a été écrit dans un langage .NET, choisissez le type de code .NET approprié, par exemple **Managed (CoreCLR)**. Si votre contrôle personnalisé a été écrit en C++, choisissez **natif**.

1. Attachez la deuxième instance de Visual Studio en cliquant sur le bouton **attacher** .

1. Dans la deuxième instance de Visual Studio, ouvrez les fichiers de code associés au contrôle personnalisé que vous souhaitez déboguer. Veillez à ouvrir simplement les fichiers, et non l’intégralité de la solution ou du projet.

1. Placez les points d’arrêt nécessaires dans les fichiers précédemment ouverts.

1. Dans la première instance de Visual Studio, fermez la page XAML contenant le contrôle personnalisé que vous souhaitez déboguer (la même page que celle que vous avez ouverte dans les étapes précédentes).

1. Dans la première instance de Visual Studio, ouvrez la page XAML que vous avez fermée à l’étape précédente. Le débogueur s’arrêtera alors au premier point d’arrêt que vous avez défini dans la deuxième instance de Visual Studio.

1. Déboguez le code dans la deuxième instance de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)