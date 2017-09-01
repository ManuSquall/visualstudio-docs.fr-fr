---
title: "Débogage avec Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: e4b8d7fb27407bf8ef4463524e9da66bac591ff4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/12/2017

---

# <a name="debugging-r-in-visual-studio"></a>Débogage de R dans Visual Studio

Les outils R pour Visual Studio (RTVS) s’intègrent au système complet de débogage de Visual Studio (consultez [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)). Cette prise en charge comprend la définition de points d’arrêt, l’attachement à des processus en cours d’exécution, l’inspection et la surveillance de variables ainsi que l’inspection de la pile des appels. Cette rubrique explore les aspects du débogage propres à R et à RTVS.

La procédure de lancement du débogueur pour le fichier R de démarrage dans un projet R est la même que celle utilisée pour d’autres types de projets. Vous pouvez donc utiliser la commande **Déboguer > Démarrer le débogage**, la touche F5 ou l’option **Fichier de démarrage source** dans la barre d’outils de débogage : 

![Bouton de démarrage du débogueur pour R](media/debugger-start-button.png)

Pour changer le fichier de démarrage, cliquez avec le bouton droit sur un fichier dans l’Explorateur de solutions et sélectionnez **Définir comme script R de démarrage**.

Dans tous les cas, le démarrage du débogueur « approvisionne » le fichier dans la fenêtre interactive, c’est-à-dire que le fichier est chargé et exécuté, comme indiqué dans la sortie de la fenêtre interactive :

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Notez que la fonction `rtvs::debug_source` est utilisée pour approvisionner le script. Cette fonction est nécessaire, car RTVS doit modifier votre code en préparation du débogage. Si vous utilisez une commande d’approvisionnement RTVS et qu’un débogueur est attaché, Visual Studio utilise automatiquement `rtvs::debug_source`.

Vous pouvez aussi attacher manuellement le débogueur directement à partir de la fenêtre interactive en utilisant l’une des commandes suivantes : **Outils R > Session > Attacher le débogueur**, **Déboguer > Joindre à la fenêtre interactive R** ou **Attacher le débogueur** (dans la barre d’outils de la fenêtre interactive). Une fois l’opération terminée, il vous appartient d’approvisionner les fichiers à déboguer. Si vous souhaitez approvisionner manuellement les fichiers, veillez à utiliser `rtvs::debug_source` à la place de la commande `source` normale dans R.

Cette connexion entre le débogueur et la fenêtre interactive facilite certaines opérations, notamment l’appel (et le débogage) d’une fonction avec des valeurs de paramètre différentes. Imaginons, par exemple, que vous avez la fonction suivante dans un fichier approvisionné (c’est-à-dire qu’il a été chargé dans la session) :

```R
add <- function(x, y) {
    return(x + y)
}
```

Définissez ensuite un point d’arrêt au niveau de l’instruction `return`. À présent, dans la fenêtre interactive, si vous entrez `add(4,5)`, le débogueur s’arrête au niveau de votre point d’arrêt.


## <a name="environment-browser-in-the-interactive-window"></a>Navigateur d’environnement dans la fenêtre interactive

Quand vous êtes arrêté dans le débogueur, vous êtes également arrêté au niveau de l’invite du navigateur d’environnement dans la [fenêtre interactive](interactive-repl.md). L’invite se présente sous la forme `Browse[n]>`, où n est un nombre.

Le navigateur d’environnement prend en charge plusieurs commandes spéciales :

| Commande | Description | 
| --- | --- |
| n | suivant : exécute l’instruction suivante dans le fichier de code (identique au pas à pas principal). |
| s | pas à pas détaillé : exécute l’instruction suivante dans le fichier de code et effectue un pas à pas détaillé dans la portée d’une fonction si l’instruction suivante est un appel de fonction. | 
| f | terminer : exécute le reste de la portée de la fonction active et retourne à l’appelant (identique au pas à pas sortant). |
| c, cont | continuer : exécute le programme jusqu’au point d’arrêt suivant. | 
| N | quitte : termine la session de débogage. |
| où | afficher la pile : affiche la pile des appels dans la fenêtre interactive. |
| help | afficher l’aide : affiche les commandes disponibles dans la fenêtre interactive. |
| &lt;expr&gt; | évaluer l’expression dans *expr*. |

![Navigateur d’environnement dans la fenêtre interactive](media/debugger-environment-browser.png)

