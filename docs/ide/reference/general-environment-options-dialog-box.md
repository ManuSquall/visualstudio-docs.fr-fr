---
title: Général, Environnement, boîte de dialogue Options
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 973e08ca6555f7da7873d3068e2794b8d34e3640
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569437"
---
# <a name="options-dialog-box-environment--general"></a>Boîte de dialogue Options : environnement \> général

Utilisez cette page pour modifier les thèmes de couleurs, les paramètres de la barre d'état et les associations d'extensions de fichier, entre autres options, pour l'environnement de développement intégré (IDE). Vous pouvez accéder à la boîte de dialogue **Options** en ouvrant le menu **Outils**, en choisissant **Options**, en ouvrant le dossier **Environnement**, puis en choisissant la page **Général**. Si cette page n’apparaît pas dans la liste, cochez la case **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

## <a name="visual-experience"></a>Expérience visuelle

**Thème de couleur**

Choisissez **Bleu**, **Clair**, **Foncé** ou **Bleu (contraste supplémentaire)** comme thème de couleur de l’IDE.

Vous pouvez installer d’autres thèmes prédéfinis et créer des thèmes personnalisés en téléchargeant et en installant l’**éditeur de thème de couleur de Visual Studio** à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Une fois cet outil installé, d'autres thèmes de couleurs apparaissent dans la zone de liste **Thème de couleur**.

**Mettre la 1ère lettre des mots en maj. dans la barre de menus**

Dans les menus, une majuscule est appliquée à la première lettre des mots par défaut. Décochez cette option pour mettre toutes les lettres des mots en majuscule.

::: moniker range=">=vs-2019"

**Optimiser le rendu pour les écrans avec des densités en pixels différentes (redémarrage nécessaire)**

Cette option active ou désactive la prise en charge des points par pouce (PPP) par écran (ou *PMA*). Lorsque la PMA est activée, l’interface utilisateur de Visual Studio s’affiche de façon nette dans n’importe quel facteur d’échelle d’affichage d’écran et n’importe quelle configuration PPP, y compris en multiécran. Pour activer la PMA, vous avez besoin de la Mise à jour d’avril 2018 de Windows 10 ou ultérieure et de .NET Framework 4.8 ou ultérieur. (Cette option apparaît grisée si ces deux prérequis ne sont pas remplis.)

> [!TIP]
> - Windows 10 comporte un paramètre **Laisser Windows essayer de résoudre les problèmes d’applications floues**. S’il est **activé**, il a effet négligeable dès lors que l’option **Optimiser le rendu des écrans présentant des densités de pixels différentes** est cochée.
> - Windows 10 inclut également une **Résolution des problèmes de compatibilité des programmes**. Nous recommandons de ne pas essayer de résoudre les problèmes d’apparence de Visual Studio avec cet utilitaire.

::: moniker-end

**Ajuster automatiquement l’expérience visuelle selon les perf. du client**

Spécifie si Visual Studio définit automatiquement le réglage de l'expérience visuelle ou si vous vous en chargez explicitement. Ce réglage peut changer l'affichage des couleurs, depuis des dégradés jusqu'à des couleurs simples, ou limiter l'utilisation des animations dans les menus ou les fenêtres contextuelles.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 comporte un paramètre **Laisser Windows essayer de résoudre les problèmes d’applications floues**. Il est recommandé **d’activer** ce paramètre si Visual Studio paraît flou sur le moniteur. Envisagez de passer à [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), qui offre une bien meilleure clarté de l’affichage. En effet, il s’agit d’une application compatible points par pouce par moniteur.

::: moniker-end

**Activer l’expérience client améliorée**

Active l'expérience visuelle complète de Visual Studio, y compris les dégradés et les animations. Désactivez cette option lors de l’utilisation de connexions Bureau à distance ou de cartes graphiques anciennes, car les performances de ces fonctionnalités peuvent se révéler médiocres dans ces cas. Cette option est disponible seulement quand vous désactivez l’option **Ajuster automatiquement l’expérience visuelle selon les perf. du client**.

**Utiliser l’accélération graphique matérielle si elle est disponible**

Utilise l'accélération graphique matérielle si elle est disponible, au lieu de l'accélération logicielle.

## <a name="other"></a>Autre

**Éléments à afficher dans le menu Fenêtre**

Personnalise le nombre de fenêtres qui s’affichent dans la liste Fenêtres du menu **Fenêtre**. Entrez un nombre compris entre 1 et 24. La valeur par défaut est de 10.

**Éléments affichés dans la liste des fichiers récents**

Personnalise le nombre des projets et des fichiers les plus récemment utilisés qui s’affichent dans le menu **Fichier**. Entrez un nombre compris entre 1 et 24. La valeur par défaut est de 10. Il s'agit d'un moyen facile de récupérer les projets et les fichiers récemment utilisés.

**Afficher la barre d’état**

Affiche la barre d'état. La barre d'état se trouve en bas de la fenêtre de l'IDE et affiche des informations sur la progression des opérations en cours.

**Le bouton Fermer n’affecte que la fenêtre Outil active**

Spécifie que quand l’utilisateur clique sur le bouton **Fermer**, seule la fenêtre Outil qui a le focus est fermée et non pas toutes les fenêtres Outil de l’ensemble ancré. Cette option est activée par défaut.

**Le bouton Masquer automatiquement n’affecte que la fenêtre Outil active**

Spécifie que quand l’utilisateur clique sur le bouton **Masquer automatiquement**, seule la fenêtre Outil qui a le focus est masquée automatiquement et non pas toutes les fenêtres Outil de l’ensemble ancré. Cette option est désactivée par défaut.

## <a name="see-also"></a>Voir aussi

- [Personnaliser les dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)
