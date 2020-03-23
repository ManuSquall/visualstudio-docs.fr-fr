---
title: REPL interactif pour R
description: Guide pratique pour utiliser l’environnement REPL interactif pour R dans Visual Studio, qui est intégré aux fenêtres de l’éditeur.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62814894"
---
# <a name="work-with-the-r-interactive-window"></a>Utiliser la fenêtre interactive R

Outils R pour Visual Studio (RTVS) comprend une fenêtre interactive R, également appelée fenêtre **REPL** (Read-Evaluate-Print-Loop), dans laquelle vous pouvez entrer du code R et voir immédiatement les résultats. Les modules, la syntaxe, les variables et les fonctionnalités IntelliSense sont tous disponibles dans la fenêtre interactive.

La fenêtre interactive est également intégrée aux fenêtres normales de l’éditeur R. Vous pouvez sélectionner le code et appuyer sur **Ctrl**+**Enter**, ou cliquer à droite et sélectionner Execute **in Interactive**, et le code est exécuté ligne par ligne dans la fenêtre interactive comme si vous l’avez tapé directement. Lorsque le curseur est sur une seule ligne dans une fenêtre d’éditeur, **Ctrl**+**Enter** envoie cette ligne à la fenêtre interactive, puis déplace le curseur vers la ligne suivante. De cette façon, vous pouvez simplement appuyer sur **Ctrl**+**Enter** à plusieurs reprises pour passer à travers le code.

Pour vous familiariser avec ces fonctionnalités, suivez la procédure pas à pas [Bien démarrer avec R](getting-started-with-r.md), ainsi que les sections de cet article. Les [extraits de code](code-snippets-for-r.md) fonctionnent aussi bien dans la fenêtre interactive que dans les fenêtres de l’éditeur R.

## <a name="overview-of-the-interactive-window"></a>Vue d’ensemble de la fenêtre interactive

Pour exécuter une ligne de code R, sous réserve que celle-ci soit valide, appuyez sur **Entrée** à la fin de la ligne :

```repl
> 3 + 3
[1] 6
```

Appuyer **sur Enter** n’importe où sur une entrée à une seule ligne exécute également cette ligne.

Toutes les entrées et sorties précédentes de la fenêtre REPL étant en lecture seule, vous ne pouvez pas les changer. Toutefois, vous pouvez à tout moment sélectionner du texte dans la fenêtre pour le copier et le coller. Le code collé est exécuté comme si vous l’aviez entré ligne par ligne.

Si vous commencez à taper une instruction et que vous appuyez sur **Entrée**, RTVS sait que l’instruction n’est pas terminée. Il passe alors en mode multiligne, affiche une invite + à gauche et applique la mise en retrait appropriée. RTVS complète également les parenthèses, les crochets et les accolades :

![Entrée d’une instruction multiligne dans la fenêtre interactive](media/repl-multiline-entry.png)

Dans ce mode multi-lignes, la clé **Enter** exécute le bloc de code uniquement lorsqu’elle est positionnée à la fin du bloc, sinon elle insère une nouvelle ligne. Toutefois, vous pouvez appuyer sur **Ctrl**+**Enter** à n’importe quelle position pour exécuter ce bloc de code immédiatement.

### <a name="toolbar-commands"></a>Commandes de la barre d’outils

Voici la fenêtre interactive avec sa barre d’outils :

![Fenêtre interactive avec sa barre d’outils](media/repl-window.png)

Les commandes de barres d’outils sont les suivantes, dont la plupart ont des équivalents clavier et sont également disponibles sur les menus **R Tools** > **Session** et **R Tools** > **Working Directory** (ou comme indiqué):

| Bouton | Commande | Combinaison de touches | Description |
| --- | --- | --- | --- |
| ![Bouton de réinitialisation](media/repl-toolbar-01-reset.png) | Réinitialiser | **Ctrl**+**Shift**+**F10** | Réinitialise la session de la fenêtre interactive. Toutes les variables et l’historique sont effacés. |
| ![Bouton Effacer](media/repl-toolbar-02-clear.png) | Désactiver | **Ctrl**+**L** | Efface la sortie affichée dans la fenêtre interactive ; n’affecte pas les variables ou l’historique de la session. |
| ![Boutons Historique](media/repl-toolbar-03-history.png) | Commande précédente de l’historique<br/>Commande suivante de l’historique | **Haut**, **Bas**<br/>**Alt**+**Up**, **Alt**+**Down** | Fait défiler l’historique, avec certains comportements pour les blocs de code multiligne. Consultez [Historique](#history). |
| ![Bouton Charger l’espace de travail](media/repl-toolbar-04-load-workspace.png) | Charger l’espace de travail | n/a | Charge un espace de travail précédemment enregistré (consultez [Espaces de travail et sessions](#workspaces-and-sessions)). |
| ![Bouton Enregistrer l’espace de travail sous](media/repl-toolbar-05-save-workspace-as.png)| Enregistrer l’espace de travail sous | n/a | Enregistre l’état actuel de la session en tant qu’espace de travail (consultez [Espaces de travail et sessions](#workspaces-and-sessions)). |
| ![Bouton Script R source](media/repl-toolbar-06-source-r-script.png) | Script R source | **Ctrl**+**Shift**+**S** | Appelle `source` avec le script R actuellement actif dans l’éditeur Visual Studio, qui exécute le code.  Ce bouton n’apparaît que si un fichier R est ouvert dans l’éditeur Visual Studio. |
| ![Bouton Script R source avec Echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Script R source avec Echo | **Ctrl**+**Shift**+**Entrez** | Identique à Approvisionner le script R, mais affiche le contenu du script dans la fenêtre interactive. |
| ![Bouton Interrompre R](media/repl-toolbar-08-interrupt-r.png)| Interrompre R | **Échap** | Arrête tout code en cours d’exécution dans la fenêtre interactive, comme la boucle `while` dans la capture d’écran affichée au début de cette section. |
| ![Bouton Attacher le débogueur](media/repl-toolbar-09b-attach-debugger.png)| Attacher le débogueur | n/a | Également disponible à l’aide de la **commande Debug** > **Attach to R Interactive.** |
| ![Bouton Définir le répertoire de travail à l’emplacement du fichier source](media/repl-toolbar-10-set-working-directory-source.png)| Définir le répertoire de travail à l’emplacement du fichier source | **Ctrl**+**Shift**+**E** | Définit le répertoire de travail à l’emplacement du dernier fichier approvisionné chargé dans la fenêtre interactive (à l’aide de `source`). Consultez [Répertoire de travail](#working-directory). |
| ![Bouton Définir le répertoire de travail à l’emplacement du projet](media/repl-toolbar-11-set-working-directory-to-project.png) | Définir le répertoire de travail à l’emplacement du projet | **Ctrl**+**Shift**+**P** | Définit le répertoire de travail à la racine du projet actuellement chargé dans Visual Studio. Consultez [Répertoire de travail](#working-directory). |
| (Champ de texte) | Sélectionner le répertoire de travail | n/a | Champ d’entrée directe pour le répertoire de travail. Consultez [Répertoire de travail](#working-directory). |

## <a name="workspaces-and-sessions"></a>Espaces de travail et sessions

L’exécution de code dans la fenêtre interactive génère un contexte dans votre session active. Le contexte est composé de variables globales, de définitions de fonctions, de charges de bibliothèque, etc. Le terme *espace de travail* désigne ce contexte. Vous pouvez enregistrer et charger des espaces de travail à tout moment.

Quand vous appuyez sur le bouton **Enregistrer l’espace de travail sous** ou sélectionnez la commande **Outils R** > **Session** > **Enregistrer l’espace de travail sous**, vous êtes invité à entrer un emplacement et un nom de fichier (extension par défaut : *.RData*).

Pour enregistrer un espace de travail sous un nom de fichier spécifique (par défaut : *.RData*), cliquez sur le bouton **Enregistrer l’espace de travail** dans la fenêtre REPL :

Pour recharger un espace de travail précédemment enregistré, sélectionnez le bouton **Charger l’espace de travail** ou utilisez **Outils R** > **Session** > **Charger l’espace de travail** et accédez au fichier d’espace de travail.

Utilisez le bouton **Réinitialiser** ou la commande **Outils R** > **Session** > **Réinitialiser** pour effacer le contexte de la session. Si vous utilisez une session à distance, la réinitialisation supprime également le profil utilisateur de l’ordinateur distant pour effacer tous les fichiers qu’il contient. (Consultez [Espaces de travail](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Répertoire de travail

Les développeurs sont souvent amenés à changer de répertoire de travail au cours d’une session interactive. Diverses commandes, disponibles sur la barre d’outils, le menu**d’annuaire** **R Tools** > Working et le menu contextuelle du projet vous permettent de définir facilement un répertoire de travail à l’emplacement d’un fichier source, de l’emplacement ou de votre projet, ou de tout autre emplacement arbitraire. Cela vous évitera de taper des noms de chemin complets ou des noms de chemin relatifs de grande taille pour faire référence aux fichiers.

## <a name="history"></a>Historique

Toutes les lignes que vous entrez dans la fenêtre interactive, notamment celles envoyées à partir d’un éditeur, sont conservées dans l’historique de la fenêtre REPL. Vous pouvez ensuite parcourir l’historique à l’aide des touches de direction Haut et Bas, comme vous êtes sans doute habitué à le faire sur la ligne de commande.

Il existe toutefois des différences. En effet, si vous commencez à taper du code sur la ligne actuelle et que vous appuyez sur la flèche Haut, la ligne actuelle est conservée dans l’historique même si elle n’a pas encore été exécutée.

L’historique dans la fenêtre interactive traite également de façon intelligente les instructions d’un autre bloc de code qui s’étendent sur plusieurs lignes. Quand vous parcourez l’historique à l’aide des touches de direction Haut et Bas, les blocs de code multilignes sont récupérés comme une unité complète et présentés comme l’entrée active. À ce stade, les touches de direction permettent de parcourir ce bloc de code ligne par ligne, jusqu’à ce que vous arriviez en haut ou en bas. En haut du bloc de code, la flèche Haut permet de récupérer l’élément précédent dans l’historique ; sur la dernière ligne, la flèche Bas permet de récupérer l’élément suivant.

Ce comportement s’adapte au cas typique de réaménage du dernier élément de l’histoire avec une flèche Up et **Entrez** la combinaison de frappes, tout en permettant naturellement l’édition d’un bloc de code multi-lignes en appuyant sur la flèche Up pour naviguer dans elle.

Pour éviter de naviguer dans des blocs de code multi-lignes, utilisez les boutons de la barre d’outils ou **Alt**+**Up** et **Alt**-**Down**, et tous ces blocs sont traités comme une seule ligne.

Le moyen le plus simple de comprendre les fonctionnalités d’historique consiste à les tester dans la fenêtre interactive. Le code ci-dessous fournit plusieurs instructions appropriées sur une ou plusieurs lignes. Veillez à copier-coller les instructions une par une pour créer l’historique approprié. (Vous pouvez également coller le code dans un fichier de code séparé, puis envoyer les lignes à la fenêtre interactive avec **Ctrl**+**Enter**.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```