---
title: Fenêtre Sortie
description: En savoir plus sur la fenêtre sortie et sur l’affichage des messages d’État pour les différentes fonctionnalités de l’IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bbc6f33c439a812d7153f48d7f20d7e1d9dd3cb1
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925161"
---
# <a name="output-window"></a>Fenêtre Sortie

La fenêtre **Sortie** affiche des messages d’état pour diverses fonctionnalités dans l’environnement de développement intégré (IDE). Pour ouvrir la fenêtre **Sortie**, dans la barre de menus, choisissez **Affichage** > **Sortie**, ou appuyez sur **Ctrl**+**Alt**+**O**.

## <a name="toolbar"></a>Barre d’outils

Les commandes suivantes sont affichées dans la barre d’outils de la fenêtre **Sortie**.

### <a name="show-output-from"></a>Afficher la sortie à partir de

Affiche un ou plusieurs volets de sortie à afficher. Plusieurs volets d’informations peuvent être disponibles, suivant les outils de l’IDE qui ont utilisé la fenêtre **Sortie** pour remettre des messages à l’utilisateur.

### <a name="find-message-in-code"></a>Rechercher le message dans le code

Déplace le point d’insertion dans l’éditeur de code vers la ligne qui contient l’erreur de build sélectionnée.

### <a name="go-to-previous-message"></a>Atteindre le message précédent

Place le focus dans la fenêtre **Sortie** sur l’erreur de build précédente et déplace le point d’insertion dans l’éditeur de code vers la ligne qui contient cette erreur de build.

### <a name="go-to-next-message"></a>Atteindre le message suivant

Place le focus dans la fenêtre **Sortie** sur l’erreur de build suivante et déplace le point d’insertion dans l’éditeur de code vers la ligne qui contient cette erreur de build.

### <a name="clear-all"></a>Tout effacer

Efface tout le texte du volet **Sortie**.

### <a name="toggle-word-wrap"></a>Activer/Désactiver le retour automatique à la ligne

Active et désactive la fonctionnalité de retour automatique à la ligne dans le volet **Sortie**. Quand cette option est activée, le texte des longues entrées qui s’étend au-delà de la zone d’affichage apparaît sur la ligne suivante.

## <a name="output-pane"></a>Volet de sortie

Le contenu du volet **Sortie** sélectionné dans la liste **Afficher la sortie à partir de** provient de la source indiquée.

## <a name="route-messages-to-the-output-window"></a>Acheminer les messages vers la fenêtre Sortie

Pour afficher la fenêtre **Sortie** chaque fois que vous générez un projet, dans la boîte de dialogue **Options**, dans la page **Projets et solutions** > **Général**, sélectionnez **Afficher la fenêtre Sortie au démarrage de la génération**. Ensuite, avec un fichier de code ouvert pour modification, choisissez **Atteindre le message suivant** et **Atteindre le message précédent** dans la barre d’outils de la fenêtre **Sortie** pour sélectionner des entrées dans le volet **Sortie**. Parallèlement, le point d’insertion dans l’éditeur de code se positionne sur la ligne de code à laquelle se produit le problème sélectionné.

Certaines fonctionnalités et commandes IDE appelées dans la [fenêtre Commande](../../ide/reference/command-window.md) remettent leur sortie à la fenêtre **Sortie**. La sortie des outils externes tels que les fichiers *.bat* et *.com*, qui s’affiche généralement dans la fenêtre de commande, est routée vers un volet **Sortie** quand vous sélectionnez l’option **Utiliser la fenêtre Sortie** dans [Gérer les outils externes](../../ide/managing-external-tools.md). D’autres types de messages peuvent également être affichés dans les volets **Sortie**. Par exemple, quand la syntaxe Transact-SQL d’une procédure stockée fait l’objet d’une vérification par rapport à une base de données cible, les résultats sont affichés dans la fenêtre **Sortie**.

Vous pouvez également programmer vos propres applications pour qu’elles écrivent les messages de diagnostic au moment de l’exécution vers un volet **Sortie**. Pour ce faire, utilisez des membres de la classe <xref:System.Diagnostics.Debug> ou <xref:System.Diagnostics.Trace> dans l’espace de noms <xref:System.Diagnostics> de l’API .NET. Les membres de la classe <xref:System.Diagnostics.Debug> affichent la sortie quand vous générez des configurations Debug de votre solution ou projet ; les membres de la classe <xref:System.Diagnostics.Trace> affichent la sortie quand vous générez des configurations Debug ou Release. Pour plus d’informations, consultez [Messages de diagnostic dans la fenêtre Sortie](../../debugger/diagnostic-messages-in-the-output-window.md).

En C++, vous pouvez créer des étapes de génération personnalisées et des événements de build dont les avertissements et erreurs sont affichés et comptabilisés dans le volet **Sortie**. En appuyant sur **F1** dans une ligne de sortie, vous pouvez afficher une rubrique d’aide appropriée. Pour plus d’informations, consultez [Mettre en forme la sortie d’une étape de génération personnalisée](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Comportement de défilement

Si vous utilisez le défilement automatique dans la fenêtre **Sortie**, puis que vous naviguez à l’aide de la souris ou des touches de direction, le défilement automatique s’arrête. Pour reprendre le défilement automatique, appuyez sur **CTRL** + **Terminer**.

## <a name="see-also"></a>Voir aussi

- [Messages de diagnostic dans la fenêtre sortie](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Guide pratique pour contrôler la fenêtre Sortie](/previous-versions/ht6z4e28(v=vs.140))
- [Compiler et générer](../../ide/compiling-and-building-in-visual-studio.md)
- [Présentation des configurations de build](../../ide/understanding-build-configurations.md)
- [Vue d'ensemble de la bibliothèque de classes](/dotnet/standard/class-library-overview)