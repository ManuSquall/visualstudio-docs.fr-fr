---
title: "Débogage avec Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>Débogage de R dans Visual Studio

Outils R pour Visual Studio (RTVS) s’intègre au système complet de débogage de Visual Studio (voir [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)). RTVS prend en charge la définition de points d’arrêt, l’attachement à des processus, l’inspection et la surveillance de variables, l’inspection de la pile des appels, etc. Cette rubrique explore les aspects du débogage propres à R et à RTVS.

La procédure de lancement du débogueur pour un fichier R de démarrage dans un projet R est la même que celle utilisée pour d’autres types de projet. Vous pouvez donc utiliser la commande **Déboguer > Démarrer le débogage**, la touche F5 ou l’option **Fichier de démarrage source** dans la barre d’outils de débogage illustrée ci-dessous. Pour changer le fichier de démarrage, cliquez avec le bouton droit sur un fichier dans l’Explorateur de solutions et sélectionnez **Définir comme script R de démarrage**.

![Bouton de démarrage du débogueur pour R](~/rtvs/media/debugger-start-button.png)

Dans tous les cas, le démarrage du débogueur « approvisionne » le fichier dans la fenêtre interactive, c’est-à-dire que le fichier est chargé et exécuté dans cette fenêtre. En fait, quand vous commencez le débogage, la fenêtre interactive affiche une sortie similaire à celle-ci :

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Notez que nous utilisons la fonction `rtvs::debug_source` pour approvisionner le script. Cette fonction est nécessaire car RTVS doit modifier votre code en préparation du débogage. Si vous utilisez l’une des commandes RTVS (par exemple, en cliquant avec le bouton droit sur un fichier dans l’Explorateur de solutions et en exécutant la commande **Approvisionner les fichier(s) sélectionné(s)**), nous redirigeons automatiquement l’appel à `rtvs::debug_source` si le débogueur est attaché.

Vous pouvez aussi attacher manuellement le débogueur directement à partir de la fenêtre interactive en utilisant l’une des commandes suivantes : **Outils R > Session > Attacher le débogueur**, **Déboguer > Joindre à la fenêtre interactive R** ou **Attacher le débogueur** (dans la barre d’outils de la fenêtre interactive). Une fois l’opération terminée, il vous appartient d’approvisionner les fichiers à déboguer. Si vous souhaitez approvisionner manuellement les fichiers, veillez à utiliser `rtvs::debug_source` à la place de la commande `source` normale dans R. Vous constaterez peut-être que celle-ci fonctionne dans _certains_ cas, mais seule la commande `rtvs::debug_source` garantit le fonctionnement du débogage dans tous les cas.

Cette connexion entre le débogueur et la fenêtre interactive facilite certaines opérations, notamment l’appel (et le débogage) d’une fonction avec des valeurs de paramètre différentes. Imaginons, par exemple, que vous avez une fonction semblable à la suivante dans un fichier approvisionné (c’est-à-dire qu’il a été chargé dans la session) :

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

![Navigateur d’environnement dans la fenêtre interactive](~/rtvs/media/debugger-environment-browser.png)

