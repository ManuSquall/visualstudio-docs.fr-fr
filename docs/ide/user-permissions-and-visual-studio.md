---
title: Autorisations utilisateur et Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6a19d67530d3cb7ac81ee00e3e65f4cce74c8d07
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2018
---
# <a name="user-permissions-and-visual-studio"></a>Autorisations utilisateur et Visual Studio

Pour des raisons de sécurité, vous devez exécuter Visual Studio en tant qu'utilisateur normal chaque fois que c'est possible.

> [!WARNING]
> Vous devez également veiller à ne pas compiler, lancer ou déboguer une solution Visual Studio qui ne provient pas d'une personne de confiance ou d'un emplacement de confiance.

Vous pouvez faire quasiment tout dans l'IDE de Visual Studio comme un utilisateur normal, mais, vous devez avoir des autorisations d'administrateur pour effectuer les tâches suivantes :

|Domaine|Tâche|Pour plus d'informations|  
|----------|----------|--------------------------|  
|Installation|Installez Visual Studio.|[Installer Visual Studio](../install/install-visual-studio.md)|  
||Installation, mise à jour ou suppression du contenu d'Aide locale.|[Installer et gérer un contenu local](../ide/install-and-manage-local-content.md)|  
|Types d'applications|Développement de solutions pour SharePoint.|[Configuration requise pour développer des solutions SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Acquisition d'une licence de développeur pour [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Obtenir une licence de développeur](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Boîte à outils|Ajout de contrôles COM classiques à la **Boîte à outils**.|[Boîte à outils](../ide/reference/toolbox.md)|  
|Compléments|Installation et utilisation des compléments qui ont été écrits à l'aide de COM classique dans l'IDE.|[Création de compléments et d’Assistants](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|Génération en cours|Utilisation des événements post-build qui inscrivent un composant.|[Présentation des étapes de génération personnalisée et des événements de build](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Inclusion d'une étape d'inscription lors de la gestion de projets C++.|[Présentation des étapes de génération personnalisée et des événements de build](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Débogage|Débogage d'applications exécutées avec des autorisations élevées.|[Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)|  
||Débogage d’applications exécutées sous un compte utilisateur différent, comme les sites web ASP.NET.|[Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Débogage dans la zone pour les applications du navigateur XAML (XBAP).|[Hôte WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|  
||Utilisation de l'émulateur pour déboguer des projets de service cloud pour Microsoft Azure.|[Débogage d’un service cloud dans Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Configuration d'un pare-feu pour un débogage distant.|[Débogage à distance](../debugger/remote-debugging.md)|  
|Outils d'analyse des performances|Profilage d'une application.|[Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)|  
|Déploiement|Déploiement d'une application web vers les Services IIS (Internet Information Services) sur un ordinateur local.|[Déploiement d’une application Web ASP.NET vers un fournisseur d’hébergement à l’aide de Visual Studio ou Visual Web Developer : déploiement vers IIS comme environnement de test](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>Exécution de Visual Studio comme administrateur

Lancez Visual Studio avec des autorisations d'administration chaque fois que vous démarrez l'IDE, ou modifiez le raccourci d'application afin qu'il soit toujours exécuté avec des autorisations d'administration. Pour plus d'informations, consultez l'aide de Windows.

### <a name="to-run-visual-studio-with-administrative-permissions"></a>Pour exécuter Visual Studio avec des autorisations d'administration

Ces instructions concernent Windows 10. Elles sont similaires pour les autres versions de Windows.

1. Ouvrez le menu **Démarrer** puis faites défiler jusqu’à Visual Studio 2017.

1. Dans le menu contextuel de **Visual Studio 2017**, sélectionnez **Plus** > **Exécuter en tant qu’administrateur**.

     Au démarrage de Visual Studio, **(Administrateur)** apparaît après le nom de produit dans la barre de titre.

## <a name="see-also"></a>Voir aussi

[Portage, migration et mise à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
[Installer Visual Studio](../install/install-visual-studio.md)
