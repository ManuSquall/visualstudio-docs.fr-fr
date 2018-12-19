---
title: 'Procédure : Installer une version spécifique | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1f8da9b0a577ba7810c3895d9492ce4be7c69cd4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065906"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Procédure : Installer une version spécifique de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nous mettons souvent à jour le programme d’installation de Visual Studio pour vous fournir la version la plus récente et optimisée de nos fonctionnalités facultatives.  Si vous préférez installer une version antérieure de Visual Studio 2015 (par exemple, une version antérieure à Visual Studio 2015 Update 1 qui inclut la prise en charge d’iOS), vous devez forcer le programme d’installation de Visual Studio à utiliser une version antérieure des fichiers manifeste de ses fonctionnalités. Cet article décrit la marche à suivre.

## <a name="installing-the-current-release"></a>Installation de la version actuelle
 Depuis la version initiale de Visual Studio 2015, nous avons mis à jour le moteur d’installation et les fichiers manifeste plusieurs fois.  Cela signifie que si vous téléchargez le programme d’installation web à partir de la [téléchargements Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) site Web sur un ordinateur propre et connecté à internet, jour permet d’installer la dernière Visual Studio 2015, qui inclut les dernières améliorations de produit ainsi que les dernières nouvelles versions des outils et des fonctionnalités facultatives.

## <a name="installing-earlier-releases"></a>Installation de versions antérieures
 Vous pouvez créer et monter une image ISO, ou vous pouvez télécharger et lancer le programme d’installation directement à partir de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , puis ajoutez le fichier .exe avec des paramètres de ligne de commande supplémentaires (telles que custominstallpath, / complète, / InstallSelectableItems, /NoRestart, etc..) pour contrôler la façon dont Visual Studio est installée.

 Le tableau suivant inclut certains scénarios spécifiques de point-à-temps et les paramètres de ligne de commande nécessaires, que vous devez passer au programme d’installation de Enterprise edition. (Vous pouvez utiliser les mêmes paramètres avec les programmes d’installation des éditions Community et Professional.)

|Édition de Visual Studio 2015|À exécuter|Ligne de commande à utiliser|Action du programme d’installation|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (dernière version publique)|Visual Studio Enterprise avec les mises à jour (disponible à partir de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Remarque :**  Cette installation fournit par défaut les fonctionnalités facultatives les plus récentes. Elle ne nécessite donc pas de paramètres de ligne de commande.|Le programme d’installation de Visual Studio utilise la dernière version du fichier feed.xml et installe les fichiers les plus récents.|
|Visual Studio Enterprise Update 3 (version Update 3 initiale sans les mises à jour ultérieures apportées à cette version)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Le programme d’installation de Visual Studio utilisera le fichier feed.xml qui était disponible au lancement de la mise à jour 3|
|Visual Studio Enterprise Update 2 (la version d’origine mise à jour 2, mais avec des mises à jour ce jour antérieures Update 3)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 3|
|Visual Studio Enterprise (2 de mise à jour d’origine sans les mises à jour de cette version 2 mise à jour supplémentaires)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilisera le fichier feed.xml qui était disponible au lancement de la mise à jour 2|
|Visual Studio Enterprise Update 1 (la version d’origine mise à jour 1, mais avec des mises à jour ce jour antérieures Update 2)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 2|
|Visual Studio Enterprise Update 1 (version Update 1 initiale sans les mises à jour ultérieures apportées à cette version)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Le programme d’installation de Visual Studio utilisera le fichier feed.xml qui était disponible au lancement de la mise à jour 1|
|Visual Studio Enterprise (version RTM initiale avec les mises à jour antérieures à la version Update 1).|Visual Studio Enterprise RTM (disponible à partir de la  [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 1.|
|Visual Studio Enterprise (version RTM initiale sans mises à jour)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Le programme d’installation de Visual Studio utilisera le fichier feed.xml qui était disponible au lancement de la version RTM|

> [!IMPORTANT]
>  Pour changer la langue de l’installation, remplacez la chaîne « enu » (correspondant à l’anglais) par l’une des valeurs suivantes :
>
> - chs (chinois simplifié)
>   -   cht (chinois traditionnel)
>   -   csy (tchèque)
>   -   deu (allemand)
>   -   esn (espagnol)
>   -   fra (français)
>   -   ita (italien)
>   -   jpa (japonais)
>   -   kor (coréen)
>   -   plk (polonais)
>   -   ptb (portugais)
>   -   rus (russe)
>   -   trk (turc)

## <a name="see-also"></a>Voir aussi
 [Guide de l’administrateur Visual Studio](../install/visual-studio-administrator-guide.md)