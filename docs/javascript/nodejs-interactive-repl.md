---
title: Utiliser l’environnement REPL Node.js
description: Visual Studio prend en charge l’interaction avec le runtime Node.js
ms.date: 12/04/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: faed930c60869010f740cf0a1e118a40299ce782
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940672"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Utilisation de la fenêtre interactive Node.js

Les outils Node.js pour Visual Studio incluent une fenêtre interactive pour le runtime Node.js installé. Cette fenêtre vous permet d’entrer le code JavaScript et d’afficher immédiatement les résultats, mais aussi d’exécuter des commandes npm pour interagir avec le projet actuel. La fenêtre interactive est également appelée REPL (**R**ead/**E**valuate/**P**rint **L**oop).

## <a name="open-the-interactive-window"></a>Ouvrir la fenêtre Interactive

Vous pouvez ouvrir la fenêtre interactive en cliquant avec le bouton droit sur le nœud de projet Node.js dans l’Explorateur de solutions, puis en sélectionnant **Open Node.js Interactive Window (Ouvrir la fenêtre interactive Node.js)**.

![Fenêtre interactive Node.js dans le menu contextuel du projet](../javascript/media/interactivewindow-open-from-project.png)

Les touches de raccourci par défaut pour ouvrir la fenêtre interactive Node.js sont **[CTRL] + K, N**. Vous pouvez aussi ouvrir la fenêtre à partir de la barre d’outils en choisissant **View (Vue)** > **Windows (Fenêtre)** > **Node.js Interactive Window (Fenêtre interactive Node.js)**.

## <a name="use-the-repl"></a>Utiliser l’environnement REPL

Une fois l’environnement ouvert, vous pouvez entrer des commandes.

![Fenêtre interactive de Node.js](../javascript/media/interactivewindow.png)

La fenêtre interactive propose plusieurs commandes prédéfinies, précédées d’un point pour les distinguer des autres fonctions JavaScript que vous déclarez. Les commandes suivantes sont prises en charge :

**.cls, .clear** : efface le contenu de la fenêtre de l’éditeur, en laissant intacts l’historique et le contexte d’exécution.

**.help** : affiche l’aide sur la commande spécifiée ou sur toutes les commandes disponibles et les combinaisons de touches si aucune commande n’est spécifiée.

**.info** : affiche des informations sur l’exécutable Node.js actuellement utilisé.

**.npm** : exécute une commande npm. Si la solution contient plusieurs projets, spécifiez le projet cible avec `.npm [projectname] <npm arguments>`.

**.reset** : rétablit l'état initial de l'environnement d'exécution, conserver l'historique.

**.save** : enregistre la session REPL actuelle dans un fichier.