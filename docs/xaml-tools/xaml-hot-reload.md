---
title: Écrire et déboguer du code XAML à l’aide du rechargement à chaud XAML
description: Le rechargement à chaud XAML, ou modifier & Continuer XAML, vous permet d’apporter des modifications à votre code XAML pendant l’exécution des applications
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b40da28cce9d2189b2f30ff6ea958926f3041836
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135077"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML dans Visual Studio

Le rechargement à chaud XAML vous permet de générer votre interface utilisateur de l’application WPF ou UWP en vous permettant d’apporter des modifications au code XAML pendant que votre application est en cours d’exécution. Le rechargement à chaud est disponible à la fois dans Visual Studio et Blend pour Visual Studio. Cette fonctionnalité vous permet de générer et de tester de façon incrémentielle du code XAML avec l’avantage du contexte de données de l’application en cours d’exécution, de l’état d’authentification et d’autres complexités réalistes qui sont difficiles à simuler au moment du Design. Si vous avez besoin d’aide pour résoudre les problèmes liés au rechargement à chaud XAML, consultez [résolution des problèmes de rechargement à chaud XAML](xaml-hot-reload-troubleshooting.md) .

> [!NOTE]
> Si vous utilisez Xamarin. Forms, consultez [rechargement à chaud XAML pour Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload).

Le rechargement à chaud XAML est particulièrement utile dans les scénarios suivants :

* Résolution des problèmes d’interface utilisateur détectés dans votre code XAML après le démarrage de l’application en mode débogage.

* Génération d’un nouveau composant d’interface utilisateur pour une application en cours de développement, tout en tirant parti du contexte d’exécution de votre application.

|Types d’applications pris en charge|Système d'exploitation et outils|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + et .NET Core</br>Windows 7 et versions ultérieures |
|Applications Windows universelles (UWP)|Windows 10 et versions ultérieures, avec le [Kit de développement logiciel (SDK) Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

L’illustration suivante montre l’utilisation de l’arborescence d’éléments visuels en direct pour ouvrir votre code source, puis le rechargement XAML pour modifier le texte du bouton et la couleur du bouton.

![Rechargement à chaud XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Le rechargement à chaud de Visual Studio XAML est actuellement pris en charge uniquement lors de l’exécution de votre application dans Visual Studio ou Blend pour Visual Studio avec le débogueur attaché (**F5** ou **Démarrer le débogage**). Vous ne pouvez pas activer cette expérience à l’aide de l' [attachement au processus](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) , sauf si vous [définissez manuellement une variable d’environnement](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Limitations connues

Voici les limitations connues du rechargement à chaud XAML. Pour contourner toute limitation que vous exécutez dans, arrêtez simplement le débogueur, puis terminez l’opération.

|Limitation|WPF|UWP|Notes|
|-|-|-|-|
|Câblage des événements aux contrôles pendant l’exécution de l’application|Non pris en charge|Non pris en charge|Voir erreur : *Vérifiez que l’événement a échoué*. Notez que, dans WPF, vous pouvez référencer un gestionnaire d’événements existant. Dans les applications UWP, le référencement d’un gestionnaire d’événements existant n’est pas pris en charge.|
|Création d’objets de ressource dans un dictionnaire de ressources, tels que ceux de la page/fenêtre ou *app. Xaml* de votre application|Prise en charge à partir de Visual Studio 2019 Update 2|Prise en charge|Exemple : ajout d’un `SolidColorBrush` dans un dictionnaire de ressources pour une utilisation en tant que `StaticResource` .</br>Remarque : les ressources statiques, les convertisseurs de style et les autres éléments écrits dans un dictionnaire de ressources peuvent être appliqués/utilisés lors de l’utilisation du rechargement à chaud XAML. Seule la création de la ressource n’est pas prise en charge.</br> Modification de la propriété du dictionnaire de ressources `Source` .|
|Ajout de nouveaux contrôles, classes, fenêtres ou autres fichiers à votre projet pendant que l’application est en cours d’exécution|Non pris en charge|Non pris en charge|None|
|Gestion des packages NuGet (ajout/suppression/mise à jour de packages)|Non pris en charge|Non pris en charge|None|
|Modification de la liaison de données qui utilise l’extension de balisage {x :Bind}|N/A|Prise en charge à partir de Visual Studio 2019|Cela nécessite Windows 10 version 1809 (Build 10.0.17763). Non pris en charge dans Visual Studio 2017 ou versions antérieures.|
|La modification des directives x :Uid n’est pas prise en charge|NON APPLICABLE|Non pris en charge|None|
|Processus multiples | Prise en charge | Prise en charge | Pris en charge dans Visual Studio 2019 [version 16,6](/visualstudio/releases/2019/release-notes-v16.6) et versions ultérieures |

## <a name="error-messages"></a>Messages d’erreur

Vous pouvez rencontrer les erreurs suivantes lors de l’utilisation du rechargement à chaud XAML.

|Message d’erreur|Description|
|-|-|
|Vérifier l’échec de l’événement|L’erreur indique que vous tentez de connecter un événement à l’un de vos contrôles, ce qui n’est pas pris en charge pendant l’exécution de votre application.|
|Cette modification n’est pas prise en charge par le rechargement à chaud XAML et ne sera pas appliquée pendant la session de débogage.|L’erreur indique que la modification que vous tentez d’effectuer n’est pas prise en charge par le rechargement à chaud XAML. Arrêtez la session de débogage, apportez la modification, puis redémarrez la session de débogage. Si vous trouvez un scénario non pris en charge que vous aimeriez voir pris en charge, utilisez notre nouvelle option « suggérer une fonctionnalité » dans la [communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Voir aussi

* [Résolution des problèmes de rechargement à chaud XAML](xaml-hot-reload-troubleshooting.md)
* [Rechargement à chaud XAML pour Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Modifier &amp; Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
