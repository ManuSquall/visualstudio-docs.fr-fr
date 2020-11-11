---
title: Visual Studio pour Mac-terminal intégré
description: Utilisation du terminal intégré dans Visual Studio pour Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: f91c2b1c3f06f8f1fbe54e32fde70b9fe88c5f5d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492869"
---
# <a name="integrated-terminal"></a>Terminal intégré
Dans Visual Studio pour Mac vous pouvez ouvrir une fenêtre de terminal intégrée, en commençant par la racine de votre solution. Le terminal peut être utile pour différents types de situations : exécution de tâches frontales (par exemple : NPM, ng ou vue), gestion des conteneurs, exécution de commandes git avancées, exécution de commandes Entity Framework, affichage de la sortie de dotnet CLI, ajout de packages NuGet, etc. 

Pour ouvrir le terminal :
- Utilisez le raccourci clavier **Ctrl + '** pour afficher ou masquer la fenêtre de terminal.
- Utilisez le menu **Afficher** le \> **Terminal** .
- Utilisez la commande de **Terminal** à partir de la barre de recherche.

![* Le Visual Studio pour Mac terminal intégré immédiatement après son lancement. *](media/integrated-terminal-intro.png)

Par défaut, quand le terminal est lancé, il effectue les opérations suivantes :
- Définissez le répertoire de travail sur le chemin d’accès de la solution actuelle.
- Chargez l’interpréteur de commandes système par défaut.

## <a name="search"></a>Recherche
Vous pouvez rechercher le contenu de la fenêtre de terminal à l’aide du menu **rechercher > Rechercher...** .

![* Recherchez l’expérience dans le Visual Studio pour Mac terminal intégré *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Raccourcis clavier de terminal
|Commandes|Raccourcis clavier|
|-|-|
|Afficher/masquer la fenêtre de terminal|**Ctrl + «**|
|Créer une instance de terminal|**Ctrl + «**|
|Faire défiler la page vers le haut|**Pg préc**|
|Faire défiler la page vers le bas|**Pg suiv**|
|Parcourir les commandes précédemment utilisées|**↑** , **↓**|
|Augmenter la taille de police|**⌘ +**|
|Réduire la taille de la police|**⌘**|

## <a name="multiple-instances"></a>Instances multiples
Plusieurs instances du terminal peuvent être en cours d’exécution à tout moment. Vous pouvez créer une nouvelle instance à l’aide du raccourci clavier **Ctrl + '** . Vous pouvez basculer entre les instances en cliquant sur l’onglet de chaque instance, ou en utilisant le raccourci **CTRL + TAB** pour utiliser la boîte de dialogue Sélecteur de fenêtre.

![* Plusieurs instances de terminal dans Visual Studio pour Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Personnalisation de la fenêtre de terminal
### <a name="configuring-the-terminal-font"></a>Configuration de la police du terminal
Vous pouvez modifier la police et la taille utilisées pour le contenu des terminaux dans le volet préférences > environnement > polices. Par défaut, la police est la même que Fenêtre Sortie contenu, à l’aide de Menlo Regular, taille 11. Vous pouvez la définir sur n’importe quelle police, indépendante de la police de votre éditeur.

![* Personnalisation des paramètres de police pour le terminal intégré *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Réutilisation des personnalisations de terminal système
Le terminal intégré utilise les mêmes valeurs par défaut et la même configuration que votre terminal système macOS. Cela signifie que vos personnalisations de terminal (zsh, Oh-My-zsh, etc.) fonctionnent également dans le terminal intégré.
