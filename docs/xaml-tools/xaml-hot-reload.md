---
title: Écrire et déboblir XAML à l’aide de XAML Hot Reload
description: XAML Hot Reload, ou XAML modifier et continuer, vous permet d’apporter des modifications à votre code XAML tout en exécutant des applications
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880092"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Écrire et déboguer le code XAML avec XAML Hot Reload dans Visual Studio

XAML Hot Reload vous aide à créer votre interface utilisateur d’application WPF ou UWP (interface utilisateur de l’application UWP) en vous permettant d’apporter des modifications au code XAML pendant que votre application est en cours d’exécution. Hot Reload est disponible dans Visual Studio et Blend for Visual Studio. Cette fonctionnalité vous permet de construire et de tester progressivement le code XAML avec l’avantage du contexte de données de l’application en cours d’exécution, l’état d’authentification, et d’autres complexités du monde réel qui est difficile à simuler pendant le temps de conception. Si vous avez besoin d’aide pour dépanner XAML Hot Reload, voir [Le dépannage XAML Hot Reload](xaml-hot-reload-troubleshooting.md) à la place.

> [!NOTE]
> Si vous utilisez Xamarin.Forms, voir [XAML Hot Reload pour Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

XAML Hot Reload est particulièrement utile dans ces scénarios :

* Correction des problèmes d’interface utilisateur trouvés dans votre code XAML après le démarrage de l’application en mode débogé.

* Construire un nouveau composant d’interface utilisateur pour une application en cours de développement, tout en profitant du contexte de fonctionnement de votre application.

|Types d’applications pris en charge|Système d'exploitation et outils|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 et .NET Core</br>Windows 7 et versions ultérieures |
|Applications Windows universelles (UWP)|Windows 10 et ci-dessus, avec le [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 |

L’illustration suivante montre l’utilisation de l’arbre visuel en direct pour ouvrir votre code source, puis XAML Hot Reload pour changer le texte du bouton et la couleur du bouton.

![Rechargement à chaud XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Hot Reload n’est actuellement pris en charge que lors de l’exécution de votre application dans Visual Studio ou Blend for Visual Studio avec le débogage attaché (**F5** ou **Start debugging**). Vous ne pouvez pas activer cette expérience en utilisant [Attach pour traiter à](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) moins que vous [définissiez manuellement une variable d’environnement.](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)

## <a name="known-limitations"></a>Limitations connues

Les limites suivantes sont connues de XAML Hot Reload. Pour contourner toute limitation que vous rencontrez, il suffit d’arrêter le débbuggeur, puis terminer l’opération.

|Limitation|WPF|UWP|Notes|
|-|-|-|-|
|Événements de câblage aux contrôles pendant que l’application est en cours d’exécution|Non pris en charge|Non pris en charge|Voir l’erreur: *Assurer l’échec de l’événement*. Notez que dans WPF, vous pouvez faire référence à un gestionnaire d’événement existant. Dans les applications UWP, le référencement d’un gestionnaire d’événements existant n’est pas pris en charge.|
|Créer des objets de ressources dans un dictionnaire de ressources tels que ceux de la Page/Fenêtre de votre application ou *app.xaml*|Pris en charge à partir de Visual Studio 2019 Mise à jour 2|Prise en charge|Exemple : `SolidColorBrush` ajouter un dictionnaire de `StaticResource`ressources pour une utilisation comme .</br>Remarque : Les ressources statiques, les convertisseurs de style et d’autres éléments écrits dans un dictionnaire de ressources peuvent être appliqués/utilisés lors de l’utilisation de XAML Hot Reload. Seule la création de la ressource n’est pas soutenue.</br> Modification de `Source` la propriété du dictionnaire des ressources.|
|Ajout de nouveaux contrôles, classes, fenêtres ou autres fichiers à votre projet pendant que l’application est en cours d’exécution|Non pris en charge|Non pris en charge|None|
|Gestion des forfaits NuGet (emballages/suppression/mise à jour)|Non pris en charge|Non pris en charge|None|
|Modification de la liaison de données qui utilise l’extension de balisage 'x:Bind'|N/A|Pris en charge à partir de Visual Studio 2019|Cela nécessite Windows 10 version 1809 (construire 10.0.17763). Non pris en charge dans Visual Studio 2017 ou les versions précédentes.|
|Modification des directives x:Uid n’est pas pris en charge|N/A|Non pris en charge|None|
|Processus multiples | Non pris en charge | Non pris en charge | Le rechargement à chaud ne peut être utilisé que contre 1 processus à la fois. |

## <a name="error-messages"></a>Messages d’erreur

Vous pouvez rencontrer les erreurs suivantes tout en utilisant XAML Hot Reload.

|Message d’erreur|Description|
|-|-|
|Assurer l’échec de l’événement|L’erreur indique que vous tentez de transférer un événement à l’un de vos contrôles, qui n’est pas pris en charge pendant que votre application est en cours d’exécution.|
|Ce changement n’est pas pris en charge par XAML Hot Reload et ne sera pas appliqué pendant la session de débogage.|L’erreur indique que la modification que vous tentez n’est pas prise en charge par XAML Hot Reload. Arrêtez la séance de débogage, effectuez le changement, puis redémarrez la séance de débogage. Si vous trouvez un scénario non pris en charge que vous souhaitez voir pris en charge, utilisez notre nouvelle option "Suggérer une fonctionnalité" dans la [communauté des développeurs de studio visuel](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Voir aussi

* [Résolution des problèmes de rechargement à chaud XAML](xaml-hot-reload-troubleshooting.md)
* [Rechargement chaud XAML pour Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Modifier & Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
