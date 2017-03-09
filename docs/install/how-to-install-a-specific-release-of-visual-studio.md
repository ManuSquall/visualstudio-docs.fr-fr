---
title: "Proc&#233;dure&#160;: installation d’une version sp&#233;cifique de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installer une version spécifique, Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Proc&#233;dure&#160;: installation d’une version sp&#233;cifique de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nous mettons souvent à jour le programme d’installation de Visual Studio pour vous fournir la version la plus récente et optimisée de nos fonctionnalités facultatives.  Si vous préférez installer une version antérieure de Visual Studio 2015 \(par exemple, une version antérieure à Visual Studio 2015 Update 1 qui inclut la prise en charge d’iOS\), vous devez forcer le programme d’installation de Visual Studio à utiliser une version antérieure des fichiers manifeste de ses fonctionnalités. Cet article décrit la marche à suivre.  
  
## Installation de la version actuelle  
 Depuis la version initiale de Visual Studio 2015, nous avons mis à jour le moteur d’installation une fois et les fichiers manifeste plus de cinq fois.  Cela signifie que si vous [téléchargez et exécutez aujourd’hui le programme d’installation de Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) sur une nouvelle machine connectée à Internet, le programme d’installation va installer Visual Studio 2015 Update 1, qui inclut les dernières améliorations du produit, ainsi que les dernières nouvelles versions des fonctionnalités et outils facultatifs.  
  
## Installation de versions antérieures  
 Vous pouvez créer et monter une image ISO, ou télécharger et lancer directement le programme d’installation web, puis ajouter le fichier .exe avec des paramètres de ligne de commande supplémentaires \(tels que \/CustomInstallPath, \/Full, \/InstallSelectableItems, \/NoRestart, etc.\) pour choisir l’installation de Visual Studio souhaitée.  
  
 Le tableau suivant présente plusieurs scénarios d’installation de versions antérieures et les paramètres de ligne de commande que vous devez transmettre au programme d’installation web de l’édition Enterprise. \(Vous pouvez utiliser les mêmes paramètres avec les programmes d’installation web des éditions Community et Professional.\)  
  
|Édition de Visual Studio 2015|À exécuter|Ligne de commande à utiliser|Action du programme d’installation|  
|-----------------------------------|----------------|----------------------------------|----------------------------------------|  
|Visual Studio Enterprise \(dernière version publique\)|Visual Studio Enterprise avec Update 1 \(disponible à partir de [VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx)\)|`vs_enterprise.exe` **Note:**  Cette installation fournit par défaut les fonctionnalités facultatives les plus récentes. Elle ne nécessite donc pas de paramètres de ligne de commande.|Le programme d’installation de Visual Studio utilise la dernière version du fichier feed.xml et installe les fichiers les plus récents.|  
|Visual Studio Enterprise \(version RTM initiale avec les mises à jour antérieures à la version Update 1\).|Visual Studio Enterprise RTM \(disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible avant la version Update 1.|  
|Visual Studio Enterprise Update 1 \(version Update 1 initiale sans les mises à jour ultérieures apportées à cette version\)|Visual Studio Enterprise avec Update 1 \(disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible dans la version Update 1.|  
|Visual Studio Enterprise \(version RTM initiale sans mises à jour\)|Visual Studio Enterprise RTM \(disponible à partir de la [page de téléchargement des abonnements MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Le programme d’installation de Visual Studio utilise le fichier feed.xml qui était disponible dans la version RTM.|  
  
> [!IMPORTANT]
>  Pour changer la langue de l’installation, remplacez la chaîne « enu » \(correspondant à l’anglais\) par l’une des valeurs suivantes :  
>   
>  -   chs \(chinois simplifié\)  
> -   cht \(chinois traditionnel\)  
> -   csy \(tchèque\)  
> -   deu \(allemand\)  
> -   esn \(espagnol\)  
> -   fra \(français\)  
> -   ita \(italien\)  
> -   jpa \(japonais\)  
> -   kor \(coréen\)  
> -   plk \(polonais\)  
> -   ptb \(portugais\)  
> -   rus \(russe\)  
> -   trk \(turc\)  
  
## Voir aussi  
 [Installation de Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)