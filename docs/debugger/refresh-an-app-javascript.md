---
title: Actualiser une application UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4bd14f0d0a8fa0697ed8fead43bac69b0b002ed3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690563"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Actualiser une application UWP dans Visual Studio

 Vous pouvez apporter des modifications à votre code pendant le débogage, puis actualiser une application UWP en JavaScript en sélectionnant le **Windows actualiser application** bouton sur le **déboguer** barre d’outils. Ce bouton permet de recharger l'application sans arrêter, ni redémarrer le débogueur. La fonctionnalité Actualiser vous permet de modifier le code HTML, CSS et JavaScript et de visualiser rapidement le résultat. Cette fonctionnalité est prise en charge pour les applications UWP.

 L'actualisation ne conserve pas l'état de votre application, ni ne reflète les modifications suivantes dans votre application :

-   modifications du fichier manifeste du package, y compris les modifications des images spécifiées dans le manifeste du package ;

-   modifications des références, telles que l'ajout ou la suppression d'une référence SDK, ou modifications des composants Windows Runtime (fichiers .winmd) ;

-   modifications des ressources, telles que les modifications des chaînes dans les fichiers .resjson ;

-   modifications des fichiers projet qui entraînent des changements de noms de chemin d’accès, de nouveaux fichiers projet ou des fichiers supprimés ;

-   modifications des propriétés de projet et d'élément, telles que les modifications du périphérique de débogage sélectionné, ou les modifications de l'action du package pour un fichier (dans la fenêtre Propriétés).

> [!IMPORTANT]
>  Lorsque vous modifiez des références ou le manifeste du package, ou que vous apportez d'autres modifications spécifiées dans la liste précédente, vous devez arrêter et redémarrer le débogueur pour mettre à jour les fichiers sources HTML, CSS et JavaScript.

### <a name="to-refresh-an-app"></a>Pour actualiser une application

1.  Votre projet UWP ouverte dans Visual Studio, sélectionnez **ordinateur Local** en tant que la cible de débogage.

     ![Liste cible de débogage sélectionnez](../debugger/media/js_select_target.png "JS_Select_Target")

3.  Appuyez sur F5 pour exécuter l'application en mode débogage.

4.  Passez dans Visual Studio.

5.  Dans la page d’accueil de votre application UWP, vous pouvez modifier certains du code HTML.

7.  Cliquez sur le **Windows actualiser application** bouton, qui ressemble à ceci : ![bouton d’application Windows Actualiser](../debugger/media/js_refresh.png "JS_Refresh"). (Ou appuyez sur F4.)

8.  Basculez vers l'application. L’application est rechargée et le code HTML mis à jour est utilisé pour restituer l’application.

## <a name="see-also"></a>Voir aussi
- [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)