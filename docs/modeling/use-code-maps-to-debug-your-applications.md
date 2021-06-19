---
title: Utiliser des cartes du code pour déboguer vos applications
description: Apprenez à utiliser des cartes de code pour éviter de perdre des bases de code volumineuses, du code inconnu ou du code hérité.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23d05240208c6160968ae0013acfdb9f2a25c973
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388553"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Utiliser des cartes du code pour déboguer vos applications

[Dans Visual Studio, les cartes de code](../modeling/map-dependencies-across-your-solutions.md) peuvent vous aider à éviter la perte de bases de code volumineuses, de code inconnu ou de code hérité. Par exemple, lorsque vous effectuez un débogage, vous devrez peut-être examiner le code dans de nombreux fichiers et projets. Utilisez des cartes de code pour naviguer parmi les éléments de code et comprendre les relations entre eux. Ainsi, vous n'avez pas à effectuer le suivi de ce code dans votre tête, ni à dessiner un diagramme distinct. Si vous devez interrompre votre travail de codage, les cartes de code vous aident à vous rafraîchir la mémoire concernant le code sur lequel vous travaillez.

![Mappage de code &#45; relations de mappage dans le code](../modeling/media/codemapstoryboardpaint.png)

**Une flèche verte indique l'emplacement de votre curseur dans l'éditeur.**

Pour plus d’informations sur les commandes et les actions que vous pouvez utiliser lorsque vous travaillez avec des cartes de code, consultez [Parcourir et réorganiser les cartes de code](../modeling/browse-and-rearrange-code-maps.md).

En savoir plus sur [le débogage dans Visual Studio avec l’outil débogueur](../debugger/debugger-feature-tour.md).

> [!NOTE]
> Pour créer et modifier des cartes de code, vous avez besoin de l’édition Visual Studio Enterprise. Dans les éditions Community et Professional de Visual Studio, vous pouvez ouvrir des diagrammes qui ont été générés dans l’édition Enterprise, mais vous ne pouvez pas les modifier.

## <a name="understand-the-problem"></a>Comprendre le problème
 Supposons qu'il existe un bogue dans un programme de dessin sur lequel vous travaillez. Pour reproduire le bogue, ouvrez la solution dans Visual Studio et appuyez sur **F5** pour démarrer le débogage.

 Quand vous dessinez une ligne et choisissez **annuler mon dernier trait**, rien ne se produit tant que vous ne dessinez pas la ligne suivante.

 ![Mappage de code &#45; bogue de reproduction](../modeling/media/codemapstoryboardpaint0.png)

 Vous commencez donc par rechercher la méthode `Undo`. Elle se trouve dans la classe `PaintCanvas`.

 ![Carte de code &#45; Rechercher du code](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Commencer à mapper le code
 Commencez maintenant à mapper la méthode `undo` et ses relations. Dans l'éditeur de code, ajoutez la méthode `undo` et les champs référencés à une nouvelle carte de code. Lorsque vous créez un mappage, l'indexation du code peut prendre un certain temps. Cela permet aux opérations ultérieures de s'exécuter plus rapidement.

 ![Carte de code &#45; afficher la méthode et les champs associés](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Le surlignage vert indique les derniers éléments ajoutés à la carte. La flèche verte indique la position de votre curseur dans le code. Les flèches situées entre les éléments représentent différentes relations. Vous pouvez obtenir plus d'informations sur les éléments qui figurent sur la carte en déplaçant la souris dessus et en examinant leurs info-bulles.

 ![Carte de code &#45; afficher les info-bulles](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Naviguer et examiner le code à partir de la carte
 Pour afficher la définition du code pour chaque champ, double-cliquez sur le champ sur la carte ou sélectionnez le champ et appuyez sur **F12**. La flèche verte se déplace entre les éléments de la carte. Votre curseur dans l'éditeur de code se déplace également automatiquement.

 ![Capture d’écran d’une fenêtre de carte de code avec le champ historique sélectionné et une fenêtre d’éditeur de code dans laquelle toutes les instances de l’historique sont mises en surbrillance.](../modeling/media/codemapstoryboardpaint5.png)

 ![Capture d’écran d’une fenêtre de carte de code avec le champ paintObjects sélectionné et une fenêtre d’éditeur de code dans laquelle toutes les instances de paintObjects sont mises en surbrillance.](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Vous pouvez également déplacer la flèche verte sur la table en déplaçant le curseur dans l'éditeur de code.

## <a name="understand-relationships-between-pieces-of-code"></a>Comprendre les relations entre les éléments de code
 Vous souhaitez maintenant déterminer quel autre code interagit avec les champs `history` et `paintObjects`. Vous pouvez ajouter toutes les méthodes qui référencent ces champs à la carte. Vous pouvez le faire à partir de la carte ou à partir de l'éditeur de code.

 ![Carte de code &#45; Rechercher toutes les références](../modeling/media/codemapstoryboardpaint6.png)

 ![Ouvrir une carte du code à partir de l’éditeur de code](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Si vous ajoutez des éléments à partir d'un projet partagé par plusieurs applications, comme Windows Phone ou Windows Store, ces éléments apparaissent toujours avec le projet d'application actif sur la carte. Ainsi, si vous changez de contexte vers un autre projet d'application, le contexte sur la carte change également pour tout élément récemment ajouté à partir du projet partagé. Les opérations que vous effectuez avec un élément de la carte s’appliquent uniquement aux éléments qui partagent le même contexte.

 Modifiez la disposition pour réorganiser le flux des relations et simplifier la lecture de la carte. Vous pouvez également déplacer des éléments sur la carte en les faisant glisser.

 ![Capture d’écran d’une fenêtre de carte de code avec le menu de disposition ouvert et la commande de gauche à Rgiht sélectionnée.](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Par défaut, la **disposition incrémentielle** est activée. Ainsi, lorsque vous ajoutez de nouveaux éléments, la carte est réorganisée au minimum. Pour réorganiser la carte entière chaque fois que vous ajoutez de nouveaux éléments, désactivez la **mise en page incrémentielle**.

 ![Capture d’écran d’une fenêtre de carte de code avec les flèches relationshiop entre les champs qui pointent de gauche à droite.](../modeling/media/codemapstoryboardpaint7.png)

 Examinons ces méthodes. Sur la carte, double-cliquez sur la méthode **PaintCanvas** , ou sélectionnez cette méthode et appuyez sur **F12**. Vous apprenez que cette méthode crée `history` et `paintObjects` sous forme de listes vides.

 ![Capture d’écran d’une fenêtre de carte de code avec la méthode PaintCanvas sélectionnée et une image d’extrait de code montrant le nom de la méthode PainCanvas mis en surbrillance.](../modeling/media/codemapstoryboardpaint8.png)

 Répétez maintenant les mêmes étapes pour examiner la définition de la méthode `clear`. Vous apprenez que `clear` effectue des tâches avec `paintObjects` et `history`. Elle appelle ensuite la méthode `Repaint`.

 ![Capture d’écran d’une fenêtre de carte de code avec la méthode Clear sélectionnée et une image d’extrait de code montrant le code pour la méthode Clear.](../modeling/media/codemapstoryboardpaint9.png)

 Examinez maintenant la définition de méthode `addPaintObject`. Elle effectue également quelques tâches avec `history` et `paintObjects`. Elle appelle également `Repaint`.

 ![Capture d’écran d’une fenêtre de carte de code avec la méthode addPaintObject sélectionnée et une image d’extrait de code montrant le code pour la méthode addPaintObject.](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Rechercher le problème en examinant la carte
 Il apparaît que toutes les méthodes qui modifient `history` et `paintObjects` appellent `Repaint`. Néanmoins la méthode `undo` n'appelle pas `Repaint`, même si `undo` modifie les mêmes champs. Vous pensez ainsi pouvoir résoudre ce problème en appelant `Repaint` depuis `undo`.

 ![Carte de code &#45; Rechercher un appel de méthode manquant](../modeling/media/codemapstoryboardpaint11.png)

 Si vous n'aviez pas de carte pour indiquer cet appel manquant, il aurait pu être plus difficile de rechercher ce problème, surtout avec un code plus complexe.

## <a name="share-your-discovery-and-next-steps"></a>Partager votre découverte et étapes suivantes
 Avant de corriger ce problème, vous pouvez rédiger des notes sur la carte à propos du problème et de la façon de le résoudre.

 ![Carte de code &#45; les éléments de commentaire et de balise pour le suivi](../modeling/media/codemapstoryboardpaint12.png)

 Par exemple, vous pouvez ajouter des commentaires à la carte et signaler des éléments à l'aide de couleurs.

 ![Carte de code &#45; éléments commentés et marqués](../modeling/media/codemapstoryboardpaint12a.png)

 Si vous avez installé Microsoft Outlook, vous pouvez envoyer la carte à d'autres personnes par courrier électronique. Vous pouvez également exporter la carte en tant qu'image ou dans un autre format.

 ![Carte de code &#45; partager, exporter, envoyer par courrier électronique](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Corriger le problème et afficher ce que vous avez fait
 Pour corriger ce bogue, ajoutez l'appel de `Repaint` à `undo`.

 ![Carte de code &#45; ajouter un appel de méthode manquant](../modeling/media/codemapstoryboardpaint14.png)

 Pour confirmer votre correction, redémarrez la session de débogage et essayez de reproduire le bogue. Maintenant, choisissez **annuler mon dernier trait** fonctionne comme prévu et confirmez que vous avez effectué le correctif correct.

 ![Carte de code &#45; correction du code de confirmation](../modeling/media/codemapstoryboardpaint15.png)

 Vous pouvez mettre à jour la carte pour afficher la correction effectuée.

 ![Carte de code &#45; mise à jour de la carte avec un appel de méthode manquant](../modeling/media/codemapstoryboardpaint16.png)

 Votre carte affiche maintenant un lien entre **Undo** et **Repaint**.

 ![Carte de code &#45; carte mise à jour avec l’appel de méthode](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Lorsque vous mettez à jour la carte, un message peut s'afficher pour indiquer que l'index de code utilisé pour créer votre carte a été mis à jour. Cela signifie que quelqu'un a modifié le code, ce qui provoque une incompatibilité de votre carte avec le code actuel. Cela ne vous empêche pas de mettre à jour la carte, mais vous devrez peut-être la recréer pour confirmer qu'elle correspond au code.

 Vous avez maintenant terminé votre investigation. Vous avez trouvé et résolu avec succès le problème en mappant le code. Vous disposez également d'une carte qui vous permet de naviguer dans le code, de vous souvenir de ce que vous avez appris et d'indiquer les mesures prises pour résoudre le problème.

## <a name="see-also"></a>Voir aussi

- [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Visualiser du code](../modeling/visualize-code.md)
