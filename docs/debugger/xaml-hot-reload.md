---
title: Écrire et déboguer du code XAML à l’aide du rechargement à chaud XAML
description: Le rechargement à chaud XAML, ou modifier & Continuer XAML, vous permet d’apporter des modifications à votre code XAML pendant l’exécution des applications
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0acacac883153990861385c96eeb3379c464f97f
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870998"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML dans Visual Studio

Le rechargement à chaud XAML vous permet de générer votre interface utilisateur de l’application WPF ou UWP en vous permettant d’apporter des modifications au code XAML pendant que votre application est en cours d’exécution. Le rechargement à chaud est disponible à la fois dans Visual Studio et Blend pour Visual Studio. Cette fonctionnalité vous permet de générer et de tester de façon incrémentielle du code XAML avec l’avantage du contexte de données de l’application en cours d’exécution, de l’état d’authentification et d’autres complexités réalistes qui sont difficiles à simuler au moment du Design.

Le rechargement à chaud XAML est particulièrement utile dans les scénarios suivants:

* Résolution des problèmes d’interface utilisateur détectés dans votre code XAML après le démarrage de l’application en mode débogage.

* Génération d’un nouveau composant d’interface utilisateur pour une application en cours de développement, tout en tirant parti du contexte d’exécution de votre application.

|Types d’applications pris en charge|Système d'exploitation et outils|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 et versions ultérieures |
|Applications Windows universelles (UWP)|Windows 10 et versions ultérieures, avec le [Kit de développement logiciel (SDK) Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Le rechargement à chaud de Visual Studio XAML est actuellement pris en charge uniquement lors de l’exécution de votre application dans Visual Studio ou Blend pour Visual Studio avec le débogueur attaché (**F5** ou **Démarrer**le débogage). Vous ne pouvez pas activer cette expérience à l’aide de l' [attachement au processus](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="known-limitations"></a>Limites connues

Voici les limitations connues du rechargement à chaud XAML. Pour contourner toute limitation que vous exécutez dans, arrêtez simplement le débogueur, puis terminez l’opération.

|Limitation|WPF|UWP|Notes|
|-|-|-|-|
|Câblage des événements aux contrôles pendant l’exécution de l’application|Non pris en charge|Non pris en charge|Voir l’erreur: *Vérifier l’échec de l’événement*|
|Création d’objets de ressource dans un dictionnaire de ressources, tels que ceux de la page/fenêtre ou *app. Xaml* de votre application|Non pris en charge|Pris en charge|Exemple: ajout d' `SolidColorBrush` un dans un dictionnaire de ressources pour une `StaticResource`utilisation en tant que.</br>Remarque : Les ressources statiques, les convertisseurs de style et les autres éléments écrits dans un dictionnaire de ressources peuvent être appliqués/utilisés lors de l’utilisation du rechargement à chaud XAML. Seule la création de la ressource n’est pas prise en charge.</br> Modification de la propriété `Source` du dictionnaire de ressources.|
|Ajout de nouveaux contrôles, classes, fenêtres ou autres fichiers à votre projet pendant que l’application est en cours d’exécution|Non pris en charge|Non pris en charge|Aucun|
|Gestion des packages NuGet (ajout/suppression/mise à jour de packages)|Non pris en charge|Non pris en charge|Aucun|
|Modification de la liaison de données qui utilise l’extension de balisage {x:Bind}|N/A|Pris en charge dans Visual Studio 2019 et versions ultérieures|Non pris en charge dans Visual Studio 2017 ou versions antérieures|

## <a name="error-messages"></a>messages d'erreur

Vous pouvez rencontrer les erreurs suivantes lors de l’utilisation du rechargement à chaud XAML.

|Message d’erreur|Description|
|-|-|
|Vérifier l’échec de l’événement|L’erreur indique que vous tentez de connecter un événement à l’un de vos contrôles, ce qui n’est pas pris en charge pendant l’exécution de votre application.|
|La commande XAML Modifier et continuer n'a trouvé aucun élément à mettre à jour.|Une erreur se produit lorsque vous modifiez du code XAML que le rechargement à chaud ne peut pas mettre à jour dans votre application.</br> Cette erreur peut parfois être corrigée à l’aide de votre application en cours d’exécution pour accéder à une vue où le code XAML est utilisé.</br> Parfois, cette erreur signifie que la modification spécifique ne peut pas être appliquée tant que vous n’avez pas redémarré la session de débogage. |
|Ce changement n'est pas pris en charge durant une session de débogage.|L’erreur indique que la modification que vous tentez d’effectuer n’est pas prise en charge par le rechargement à chaud XAML. Arrêtez la session de débogage, apportez la modification, puis redémarrez la session de débogage.|
