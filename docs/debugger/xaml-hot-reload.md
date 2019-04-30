---
title: Écrire et déboguer le XAML à l’aide de rechargement à chaud de XAML
description: Recharger à chaud de XAML ou XAML modifier et continuer, vous permet d’apporter des modifications à votre code XAML pendant l’exécution des applications
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a002c3876eecf0f31a8d104fa235b1208af90699
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929129"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Écrire et déboguer du code XAML en cours d’exécution avec le recharger à chaud de XAML dans Visual Studio

XAML de Visual Studio à chaud recharger vous permet de créer votre interface utilisateur des applications WPF ou UWP en vous permettant d’apporter des modifications au code XAML pendant l’exécution de votre application. Cette fonctionnalité vous permet de façon incrémentielle générer et tester le code XAML avec l’avantage de contexte de données de l’application en cours d’exécution, l’état de l’authentification et autres complexité réelle qui est difficile à simuler au moment du design.

Recharger à chaud XAML est particulièrement utile dans ces scénarios :

* Résolution des problèmes de l’interface utilisateur trouvés dans votre code XAML, une fois que l’application a été démarrée en mode débogage.

* La création d’un nouveau composant de l’interface utilisateur pour une application est en cours de développement, tout en tirant parti de votre application contexte d’exécution.

|Types d’applications pris en charge|Système d'exploitation et outils|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 et versions ultérieures |
|Applications Windows universelle (UWP)|Windows 10 et versions ultérieures, avec le [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Rechargement de chaud Visual Studio XAML est actuellement pris en charge uniquement lors de l’exécution de votre application dans Visual Studio avec le débogueur attaché (**F5** ou **démarrer le débogage**). Vous ne pouvez pas activer cette expérience à l’aide de *attacher au processus*.

## <a name="known-limitations"></a>Limitations connues

Les éléments suivants sont connus limitations de XAML à chaud recharger. Pour éviter toute limitation que vous rencontrez, simplement arrêter le débogueur, puis terminez l’opération.

|Limitation|WPF|UWP|Notes|
|-|-|-|-|
|Connexion des événements aux contrôles pendant l’exécution de l’application|Non prise en charge|Non pris en charge|Consultez l’erreur : *Vérifiez l’événement a échoué*|
|Création d’objets de ressource dans un dictionnaire de ressources, telles que celles dans la fenêtre de la Page de votre application ou *App.xaml*|Non prise en charge|Prise en charge|Exemple : ajout d’un ```SolidColorBrush``` dans un dictionnaire de ressources pour une utilisation comme un ```StaticResource```.</br>Remarque : Ressources statiques, les convertisseurs de style et les autres éléments écrits dans un dictionnaire de ressources peuvent être appliqué/utilisé lors de l’utilisation de rechargement à chaud de XAML. Uniquement la création de la ressource n’est pas pris en charge.</br> Modifier le dictionnaire de ressources ```Source``` propriété.| 
|Ajout de nouveaux contrôles, de classes, de windows ou d’autres fichiers à votre projet pendant l’exécution de l’application|Non prise en charge|Non prise en charge|Aucun.|
|La gestion des packages NuGet (Ajout/Suppression/mise à jour des packages)|Non prise en charge|Non prise en charge|Aucun.|
|Modification de liaison de données qui utilise l’extension de balisage {x : Bind}|N/A|Prise en charge dans Visual Studio 2019 et versions ultérieures|Non pris en charge dans Visual Studio 2018 ou des versions antérieures|

## <a name="error-messages"></a>Messages d’erreur

Vous êtes susceptible de rencontrer les erreurs suivantes lors de l’utilisation de rechargement à chaud de XAML.

|Message d'erreur|Description|
|-|-|-|
|Vérifiez l’événement a échoué|Erreur indique que vous essayez d’associer un événement à un de vos contrôles, ce qui n’est pas pris en charge pendant l’exécution de votre application.|
|La commande XAML Modifier et continuer n'a trouvé aucun élément à mettre à jour.|Erreur se produit lors de la modification XAML recharger à chaud ne peut pas mettre à jour dans votre application.</br> Cette erreur peut parfois être résolue à l’aide de votre application en cours d’exécution pour accéder à une vue où le XAML est utilisé.</br> Parfois, cette erreur signifie que la modification spécifique ne peut pas être appliquée jusqu'à ce que vous redémarrez la session de débogage. |
|Ce changement n'est pas pris en charge durant une session de débogage.|Erreur indique que la modification que vous essayez de ne prend pas en charge recharger à chaud de XAML. Arrêter la session de débogage, apporter la modification, puis redémarrez la session de débogage.|