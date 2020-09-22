---
title: 'Procédure : installer une version spécifique | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839853"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Procédure : installation d’une mise en production spécifique de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nous mettons souvent à jour le programme d’installation de Visual Studio pour vous fournir la version la plus récente et optimisée de nos fonctionnalités facultatives.  Si vous préférez installer une version antérieure de Visual Studio 2015 (par exemple, une version antérieure à Visual Studio 2015 Update 1 qui inclut la prise en charge d’iOS), vous devez forcer le programme d’installation de Visual Studio à utiliser une version antérieure des fichiers manifeste de ses fonctionnalités. Cet article décrit la marche à suivre.

## <a name="installing-the-current-release"></a>Installation de la version actuelle
 Depuis la mise en production initiale de Visual Studio 2015, nous avons mis à jour le moteur d’installation et les fichiers manifeste plusieurs fois.  Cela signifie que si vous téléchargez le programme d’installation web à partir du site web [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) sur un ordinateur connecté à Internet, le programme d’installation installe la mise à jour de Visual Studio 2015 la plus récente, qui inclut les dernières améliorations du produit, ainsi que les dernières nouvelles versions des fonctionnalités et outils facultatifs.

## <a name="installing-earlier-releases"></a>Installation de versions antérieures
 Vous pouvez créer et monter une image ISO, ou télécharger et lancer directement le programme d’installation à partir de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), puis ajouter le fichier .exe avec des paramètres de ligne de commande supplémentaires (tels que /CustomInstallPath, /Full, /InstallSelectableItems, /NoRestart, etc.) pour contrôler la façon dont Visual Studio est installé.

 Le tableau suivant présente plusieurs scénarios d’installation de versions antérieures et les paramètres de ligne de commande que vous devez transmettre au programme d’installation de l’édition Enterprise. (Vous pouvez utiliser les mêmes paramètres avec les programmes d’installation des éditions Community et Professional.)

|Édition de Visual Studio 2015|À exécuter|Ligne de commande à utiliser|Action du programme d’installation|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (dernière version publique)|Visual Studio Enterprise avec mises à jour (disponible à partir de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Remarque :**  Cette installation fournit par défaut les fonctionnalités facultatives les plus récentes. Elle ne nécessite donc pas de paramètres de ligne de commande.|Le programme d’installation de Visual Studio utilise la dernière version du fichier feed.xml et installe les fichiers les plus récents.|
|Visual Studio Enterprise Update 3 (version Update 3 initiale sans les mises à jour ultérieures apportées à cette version)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible lors de la mise en production de Update 3|
|Visual Studio Enterprise Update 2 (version Update 2 d’origine, mais avec les mises à jour antérieures à la version Update 3)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 3|
|Visual Studio Enterprise (version Update 2 initiale sans les mises à jour ultérieures apportées à cette version)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible lors de la mise en production de Update 2|
|Visual Studio Enterprise Update 1 (version Update 1 d’origine, mais avec les mises à jour antérieures à la version Update 2)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 2|
|Visual Studio Enterprise Update 1 (version Update 1 initiale sans les mises à jour ultérieures apportées à cette version)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible lors de la mise en production de Update 1|
|Visual Studio Enterprise (version RTM initiale avec les mises à jour antérieures à la version Update 1).|Visual Studio Enterprise RTM (disponible à partir de la  [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 1.|
|Visual Studio Enterprise (version RTM initiale sans mises à jour)|Visual Studio Enterprise RTM (disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible lors de la mise en production de RTM|

> [!IMPORTANT]
> Pour changer la langue de l’installation, remplacez la chaîne « enu » (correspondant à l’anglais) par l’une des valeurs suivantes :
>
> - chs (chinois simplifié)
>   - cht (chinois traditionnel)
>   - csy (tchèque)
>   - deu (allemand)
>   - esn (espagnol)
>   - fra (français)
>   - ita (italien)
>   - jpa (japonais)
>   - kor (coréen)
>   - plk (polonais)
>   - ptb (portugais)
>   - rus (russe)
>   - trk (turc)

## <a name="see-also"></a>Voir aussi
 [Guide de l’Administrateur Visual Studio](../install/visual-studio-administrator-guide.md)