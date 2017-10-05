---
title: "Installation de Visual Studio derrière un pare-feu ou un serveur proxy | Microsoft Docs"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 1e017806ca7bf3d23410ba3a2f999dca0b78f240
ms.openlocfilehash: cb2ef641cb5b9b6efbd1aeb539154da1e4082b51
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Installation de Visual Studio derrière un pare-feu ou un serveur proxy

Le programme d’installation de Visual Studio télécharge les fichiers de différents domaines et de leurs serveurs de téléchargement. Cette page répertorie les URL de domaine que vous voudrez éventuellement ajouter dans la liste approuvée de vos scripts de déploiement.

Si c’est possible pour votre environnement, ajoutez les domaines suivants avec les deux protocoles HTTP et HTTPS.

## <a name="microsoft-domains"></a>Domaines Microsoft
| Domaine | Objectif |
| ------ | ------- |
| go.microsoft.com | Résolution de l’URL d’installation |
| aka.ms | Résolution de l’URL d’installation |
| download.visualstudio.microsoft.com | Emplacement de téléchargement des packages d’installation |
| download.microsoft.com | Emplacement de téléchargement des packages d’installation |
| download.visualstudio.com | Emplacement de téléchargement des packages d’installation |
| dl.xamarin.com | Emplacement de téléchargement des packages d’installation |
| visualstudiogallery.msdn.microsoft.com | Emplacement de téléchargement des extensions Visual Studio |
| www.visualstudio.com | Emplacement de la documentation |
| docs.microsoft.com | Emplacement de la documentation |
| msdn.microsoft.com | Emplacement de la documentation |
| www.microsoft.com | Emplacement de la documentation |
| *.windows.net | Emplacement de connexion |
| *.microsoftonline.com | Emplacement de connexion |
| *.live.com | Emplacement de connexion |


## <a name="non-microsoft-domains"></a>Domaines non-Microsoft
| Domaine | Installe ces charges de travail |
| ------ | ------- |
| archive.apache.org |  Développement mobile avec JavaScript <br />(Cordova) |
| cocos2d-x.org | Développement de jeux avec C++ <br />(Cocos) |
| download.epicgames.com | Développement de jeux avec C++ <br />(Unreal Engine) |
| download.oracle.com | Développement mobile avec JavaScript <br />(Java SDK) <br /><br />Développement mobile en .NET <br />(Java SDK) |
| download.unity3d.com | Développement de jeux avec Unity <br />(Unity) |
| netstorage.unity3d.com | Développement de jeux avec Unity <br /> (Unity) |
| dl.google.com | Développement mobile avec JavaScript <br />(Android SDK et NDK, émulateur) <br /><br />Développement mobile en .NET <br />(Android SDK et NDK, émulateur) |
| www.incredibuild.com | Développement de jeux avec C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Développement de jeux avec C++ <br />(IncrediBuild) |
| www.python.org | Développement Python <br />(Python) <br /><br />Applications de science des données et analytiques <br />(Python) |

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
  * [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
    * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
    * [Informations de référence sur les ID de charge de travail et de composant](workload-and-component-ids.md)
  * [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md)
    * [Considérations particulières relatives à l’installation de Visual Studio dans un environnement hors connexion](install-visual-studio-in-offline-environment.md)
  * [Automatiser Visual Studio avec un fichier réponse](automated-installation-with-response-file.md)
  * [Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [Définir les valeurs par défaut des déploiements d’entreprise de Visual Studio](set-defaults-for-enterprise-deployments.md)
  * [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md)
  * [Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)
  * [Contrôler les mises à jour applicables aux déploiements de Visual Studio](controlling-updates-to-visual-studio-deployments.md)
  * [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
  * [Signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

