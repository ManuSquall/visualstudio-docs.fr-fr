---
title: Installer et utiliser Visual Studio pour Mac avec un pare-feu ou un serveur proxy
titleSuffix: ''
description: Ce document présente la liste des hôtes qui doivent figurer dans la liste verte du pare-feu pour permettre à Visual Studio pour Mac (et ses charges de travail, dont Xamarin) de fonctionner dans un environnement professionnel.
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 25a4597c8d523b63e7ceb0cf8b5eff71af58071a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800409"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installer et utiliser Visual Studio pour Mac derrière un pare-feu ou un serveur proxy

Si vous ou votre organisation utilisez des mesures de sécurité comme un pare-feu ou un serveur proxy, vous pouvez souhaiter ajouter des domaines à une « liste verte » et ouvrir des ports et des protocoles afin de bénéficier d’une expérience optimale pendant l’installation et l’utilisation de Visual Studio pour Mac et des services Azure.

- [**Installer Visual Studio pour Mac**](#install-visual-studio-for-mac): ces tables incluent les domaines qui doivent autoriser la connectivité afin que vous ayez accès à toutes les fonctionnalités et charges de travail de Visual Studio pour Mac.

- [**Utilisez Visual Studio pour Mac**](#use-visual-studio-for-mac): ces tables incluent des domaines qui doivent autoriser la connectivité afin que vous ayez accès aux fonctionnalités associées.

## <a name="install-visual-studio-for-mac"></a>Installer Visual Studio pour Mac

Dans la mesure où le programme d’installation de Visual Studio pour Mac effectue des téléchargements sur différents domaines et serveurs de téléchargement, voici les domaines et les URL que vous pouvez marquer comme approuvés dans vos configurations.

### <a name="microsoft-domains"></a>Domaines Microsoft

| Domain| Objectif |
| ----------------------------------- |---------------------------|
| *.live.com| Gestion des informations d’identification |
| app.vssps.visualstudio.com| Métadonnées du programme d’installation|
| vortex.data.microsoft.com | Rapports d’incidents et d’erreurs |
| az667904.vo.msecnd.net| Rapports d’incidents et d’erreurs |
| xamarin.com | Métadonnées du programme d’installation|
| xampubdl.blob.core.windows.net| Packages du programme d’installation|
| download.visualstudio.microsoft.com | Packages du programme d’installation|
| xamarin.azureedge.net | Packages du programme d’installation|
| developer.xamarin.com | Packages du programme d’installation|
| static.xamarin.com | Packages du programme d’installation|
| dl.xamarin.com | Packages du programme d’installation|
| dc.services.visualstudio.com| Rapports d’incidents |

### <a name="third-party-domains"></a>Domaines tiers

| Domain| Objectif |
| --------------------------|-------------------------|
| dl.google.com | Kit de développement logiciel Android |
| download.oracle.com | Kit de développement logiciel (SDK) Java|
| api.apple-cloudkit.com| Services de sécurité Apple |

## <a name="use-visual-studio-for-mac"></a>Utiliser Visual Studio pour Mac

Nous vous recommandons, pour avoir accès à toutes les fonctionnalités dont vous avez besoin dans Visual Studio pour Mac derrière un proxy ou un pare-feu, de mettre sur liste verte les domaines et ports suivants.

### <a name="general"></a>Général

| Domaine | Port(s)|Objectif|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Résolution d’URL Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Données de la page de démarrage|
| software.xamarin.com |  80/443|Service de mise à jour|
| addins.monodevelop.com | 80/443| Services d’extension |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Notifications et fonctionnalité expérimentale |
| targetednotifications.azurewebsites.net|  80/443| Permet de filtrer une liste de notifications globale sur une liste qui s’applique uniquement à certains types de scénarios de machines/d’utilisation|

### <a name="identity"></a>Identité

| Domaine | Port(s)|Objectif|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Fournisseur d’identité|
| secure.aadcdn.microsoftonline-p.com | 80/443|Fournisseur d’identité|
| dc.services.visualstudio.com| 80/443|Rapports d’incidents|
| management.azure.com|80/443| API des services Azure |

### <a name="nuget"></a>NuGet

| Domaine | Port(s)|Objectif|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|API NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Fournisseur d’identité|

### <a name="android-projects"></a>Projets Android

| Domain| Objectif|
| ------------------------------------|------------------------------------|
| time.android.com| Serveur de temps pour l’Émulateur Android |
| connectivitycheck.gstatic.com | Connectivité pour l’Émulateur Android|
| cloudconfig.googleapis.com| API pour l’Émulateur Android|

## <a name="see-also"></a>Voir aussi

- [Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Résoudre des problèmes similaires sur Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
