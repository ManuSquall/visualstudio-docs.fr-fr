---
title: Exécuter en tant qu'administrateur
description: Découvrez comment exécuter Visual Studio en tant qu’administrateur.
ms.date: 01/06/2020
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63787b394d9e8988759cd141540785e34324f8c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971295"
---
# <a name="user-permissions-and-visual-studio"></a>Autorisations utilisateur et Visual Studio

Pour des raisons de sécurité, vous devez exécuter Visual Studio en tant qu’utilisateur typique dans la mesure du possible.

> [!WARNING]
> Vous devez également veiller à ne pas compiler, lancer ou déboguer une solution Visual Studio qui ne provient pas d'une personne de confiance ou d'un emplacement de confiance.

Vous pouvez faire presque tout dans l’IDE de Visual Studio en tant qu’utilisateur standard. Vous avez besoin d’autorisations d’administrateur pour effectuer les tâches suivantes :

|Domaine|Tâche|Informations supplémentaires|
|----------|----------| - |
|Installation|Installez ou modifiez Visual Studio.|[Installer Visual Studio](../install/install-visual-studio.md), [modifier Visual Studio](../install/modify-visual-studio.md)|
||Installer, mettre à jour ou supprimer le contenu d’aide locale.|[Installer et gérer le contenu d’aide locale](../help-viewer/install-manage-local-content.md)|
|Boîte à outils|Ajouter des contrôles COM classiques à la **Boîte à outils**.|[Boîte à outils](../ide/reference/toolbox.md)|
|Génération|Utiliser des événements post-build qui inscrivent un composant.|[Présentation des étapes de build personnalisée et des événements de build](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Inclure une étape d’inscription lors de la gestion de projets C++.||
|Débogage|Déboguer des applications exécutées avec des autorisations élevées.|[Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)|
||Déboguer des applications exécutées sous un compte d’utilisateur différent, comme les sites web ASP.NET.|[Déboguer des applications ASP.NET et AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Déboguer dans la zone pour les applications du navigateur XAML (XBAP).|[Hôte WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Utiliser l’émulateur pour déboguer des projets de service cloud pour Microsoft Azure.|[Déboguer un service cloud dans Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Configurer un pare-feu pour le débogage distant|[Débogage distant](../debugger/remote-debugging.md)|
|Outils d'analyse des performances|Attachement à une application avec élévation de privilèges.|[Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)|
||Utilisez le profileur GPU.|[Profilage du GPU](../profiling/gpu-usage.md)|
|Déploiement|Déployer une application web sur les Services IIS (Internet Information Services) sur un ordinateur local.|[Déployer une application web ASP.NET à l’aide de Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Exécuter Visual Studio en tant qu’administrateur

Si vous avez besoin d’exécuter Visual Studio en tant qu’administrateur, suivez ces étapes pour ouvrir l’IDE :

> [!NOTE]
> Ces instructions concernent Windows 10. Elles sont similaires pour les autres versions de Windows.

::: moniker range="vs-2017"

1. Ouvrez le menu **Démarrer** puis faites défiler jusqu’à Visual Studio 2017.

1. Dans le menu contextuel de **Visual Studio 2017**, sélectionnez **Plus** > **Exécuter en tant qu’administrateur**.

   Au démarrage de Visual Studio, **(Administrateur)** apparaît après le nom de produit dans la barre de titre.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez le menu **Démarrer**, puis faites défiler jusqu’à Visual Studio 2019.

1. Dans le menu contextuel de **Visual Studio 2019**, sélectionnez **Plus** > **Exécuter en tant qu’administrateur**.

   Au démarrage de Visual Studio, **(Administrateur)** apparaît après le nom de produit dans la barre de titre.

::: moniker-end

Vous pouvez également modifier le raccourci de l’application afin de toujours l’exécuter avec des autorisations administratives.

## <a name="see-also"></a>Voir aussi

- [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Installer Visual Studio](../install/install-visual-studio.md)
