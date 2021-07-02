---
title: Expériences connectées dans Visual Studio
description: Une expérience connectée se connecte à Internet à partir d’un ordinateur client et fournit un service au client.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 689fc40be8aee959023777a3fac6d9134ee979ea
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222888"
---
# <a name="connected-experiences-in-visual-studio"></a>**Expériences connectées dans Visual Studio** #

Visual Studio est constitué d’applications logicielles clientes et d’expériences connectées conçues pour vous permettre de coder plus efficacement. la mise à jour d’un package [NuGet](/nuget/consume-packages/install-use-packages-visual-studio) , la sélection d’une suggestion [IntelliCode](/visualstudio/intellicode/overview) et la collaboration avec un autre développeur par le biais de [Live Share](/visualstudio/liveshare/quickstart/share) sont des exemples d’expériences connectées. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Indiquez si ces expériences connectées peuvent être utilisées ##

Vous pouvez choisir les expériences connectées à utiliser. l’utilisation de certaines expériences connectées nécessite un accord à des termes différents et supplémentaires au cluf Visual Studio. Ces expériences peuvent être des services en ligne et/ou des services appartenant à Microsoft appartenant à des tiers. par exemple, lorsque vous utilisez GitHub des expériences connectées, la [déclaration de confidentialité de GitHub](https://docs.github.com/github/site-policy/github-privacy-statement) et les [conditions d’utilisation de GitHub](https://docs.github.com/github/site-policy/github-terms-of-service), GitHub conditions d' [utilisation d’entreprise](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)et/ou [des termes de produit supplémentaires](https://docs.github.com/github/site-policy/github-additional-product-terms) s’appliquent. Si vous [Signalez un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio), vous acceptez les [conditions d’utilisation](https://www.microsoft.com/legal/terms-of-use) et la [déclaration de confidentialité](https://privacy.microsoft.com/en-us/privacystatement)Microsoft. si vous utilisez le service NuGet, vous acceptez les [conditions d’utilisation NuGet](https://www.nuget.org/policies/Terms) et la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/en-us/privacystatement). 

lorsque vous installez Visual Studio, [vous pouvez éventuellement sélectionner les charges de travail et les composants à installer](/visualstudio/install/install-visual-studio). Les charges de travail et les composants peuvent tirer parti d’un logiciel tiers, et ils peuvent activer les expériences connectées, en fonction de leur fonctionnalité. Par exemple, [le téléchargement de la charge de travail de développement Azure vous permet de publier vos applications Cloud dans Azure](https://visualstudio.microsoft.com/vs/features/azure/). En fonction de vos sélections d’installation, vous pouvez également utiliser le menu Outils et options pour vous connecter à, pour configurer et pour utiliser les expériences connectées. Par exemple, vous pouvez vous connecter à un serveur, ajouter l’authentification des services Azure ou modifier les paramètres IntelliCode ou LiveShare.  

Vous pouvez également utiliser les paramètres de [pare-feu](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) de votre organisation pour activer ou désactiver la connexion aux services. notez que la désactivation de la connexion à un point de terminaison peut affecter ou désactiver les performances des fonctionnalités de Visual Studio associées. 

enfin, la place de marché Visual Studio propose des extensions qui peuvent permettre des expériences connectées de premier ou troisième tiers. Visual Studio marketplace est soumis aux [conditions d’utilisation de la place de marché Visual Studio](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) et à la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/en-us/privacystatement). Chaque extension nécessite un accord à des conditions d’utilisation particulières et une déclaration de confidentialité associée à cette offre.  


## <a name="required-service-data"></a>Données de service requises ##

Les données de service requises peuvent inclure des informations relatives au fonctionnement de l’expérience connectée qui est nécessaire pour garantir la sécurité, la mise à jour et l’exécution du service sous-jacent comme prévu. Si vous choisissez d’utiliser une expérience connectée qui analyse votre contenu, par exemple IntelliCode, le code que vous avez sélectionné pour votre modèle est également envoyé et traité pour vous fournir l’expérience connectée. les données de service requises peuvent également inclure les informations nécessaires à une expérience connectée pour effectuer sa tâche, par exemple la mise à jour d’un package de NuGet. Vous pouvez gérer les données de service requises en choisissant si vous souhaitez ou non utiliser un service particulier. Si vous n’utilisez pas de service, aucune donnée de service requise n’est collectée. 

Les données de service requises sont différentes des données de diagnostic, car les données de diagnostic sont liées au logiciel exécuté sur votre appareil. vous avez le choix entre participer aux [contrôles de confidentialité Visual Studio Programme d’amélioration des services (VSCEIP) pour les données de diagnostic](/visualstudio/ide/visual-studio-experience-improvement-program), mais ce paramètre n’a aucune incidence sur l’envoi des données de service requises. 

## <a name="diagnostic-data-collection"></a>Collecte des données de diagnostic ##

les données de Diagnostic sont utilisées pour conserver les Visual Studio sécurisés et à jour, détecter, diagnostiquer et résoudre les problèmes, et également apporter des améliorations au produit. les données de Diagnostic sont collectées et envoyées à Microsoft à propos de Visual Studio logiciel client s’exécutant sur l’appareil de l’utilisateur.

Lorsque vous désabonnez, vous désabonnez de la collection de données de diagnostic facultative. une collecte de données de diagnostic est nécessaire pour s’assurer que Visual Studio est sécurisé, à jour et qu’il fonctionne comme prévu. La collecte de données de diagnostic requise n’est pas affectée par votre choix pour refuser l' [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program). 
