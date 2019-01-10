---
title: Général, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15af9d627e425df57443cbf663b2b231b74f9a7e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945533"
---
# <a name="general-environment-options-dialog-box"></a>Général, Environnement, boîte de dialogue Options

Utilisez cette page pour modifier les thèmes de couleurs, les paramètres de la barre d'état et les associations d'extensions de fichier, entre autres options, pour l'environnement de développement intégré (IDE). Vous pouvez accéder à la boîte de dialogue **Options** en ouvrant le menu **Outils**, en choisissant **Options**, en ouvrant le dossier **Environnement**, puis en choisissant la page **Général**. Si cette page n’apparaît pas dans la liste, cochez la case **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

## <a name="visual-experience"></a>Expérience visuelle

**Thème de couleur**

Choisissez le thème de couleur **Bleu**, **Clair** ou **Sombre** pour l’IDE.

Vous pouvez installer d’autres thèmes prédéfinis et créer des thèmes personnalisés en téléchargeant et en installant **l’éditeur de thème de couleur de Visual Studio** à partir de la [Place de marché Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Une fois cet outil installé, d'autres thèmes de couleurs apparaissent dans la zone de liste des thèmes de couleurs.

**Appliquer une 1ère lettre en majuscule à la barre de menus**

Les initiales des menus sont en **majuscules** par défaut. Désélectionnez cette option pour les définir sur **Tout en majuscules**.

**Ajuster automatiquement l’expérience visuelle selon les perf. du client**

Spécifie si Visual Studio définit automatiquement le réglage de l'expérience visuelle ou si vous vous en chargez explicitement. Ce réglage peut changer l'affichage des couleurs, depuis des dégradés jusqu'à des couleurs simples, ou limiter l'utilisation des animations dans les menus ou les fenêtres contextuelles.

**Activer l’expérience client améliorée**

Active l'expérience visuelle complète de Visual Studio, y compris les dégradés et les animations. Désactivez cette option lors de l’utilisation de connexions Bureau à distance ou de cartes graphiques anciennes, car les performances de ces fonctionnalités peuvent se révéler médiocres dans ces cas. Cette option est disponible seulement quand vous désactivez l’option **Ajuster automatiquement l’expérience visuelle selon les perf. du client**.

**Utiliser l’accélération graphique matérielle si elle est disponible**

Utilise l'accélération graphique matérielle si elle est disponible, au lieu de l'accélération logicielle.

## <a name="other"></a>Autre

**Éléments affichés dans le menu Fenêtre**

Personnalise le nombre de fenêtres qui s’affichent dans la liste Fenêtres du menu **Fenêtre**. Entrez un nombre compris entre 1 et 24. Par défaut, ce nombre est de 10.

**Éléments affichés dans la liste des fichiers récents**

Personnalise le nombre des projets et des fichiers les plus récemment utilisés qui s’affichent dans le menu **Fichier**. Entrez un nombre compris entre 1 et 24. Par défaut, ce nombre est de 10. Il s'agit d'un moyen facile de récupérer les projets et les fichiers récemment utilisés.

**Afficher la barre d’état**

Affiche la barre d'état. La barre d'état se trouve en bas de la fenêtre de l'IDE et affiche des informations sur la progression des opérations en cours.

**Le bouton Fermer n’affecte que la fenêtre Outil active**

Spécifie que quand l’utilisateur clique sur le bouton **Fermer**, seule la fenêtre Outil qui a le focus est fermée et non pas toutes les fenêtres Outil de l’ensemble ancré. Cette option est activée par défaut.

**Le bouton Masquer automatiquement n’affecte que la fenêtre Outil active**

Spécifie que quand l’utilisateur clique sur le bouton **Masquer automatiquement**, seule la fenêtre Outil qui a le focus est masquée automatiquement et non pas toutes les fenêtres Outil de l’ensemble ancré. Cette option est désactivée par défaut.

## <a name="see-also"></a>Voir aussi

- [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)
- [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)