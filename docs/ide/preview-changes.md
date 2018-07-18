---
title: Aperçu des changements de code dans Visual Studio
ms.date: 12/16/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: dfb9ff26ca20060a8df9a0b3a81783b60e0b46f3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942453"
---
# <a name="preview-changes-window"></a>Fenêtre Aperçu des modifications

Quand vous utilisez différents outils de *Refactorisation* ou *Actions rapides* dans Visual Studio, il est souvent possible d’afficher un aperçu des modifications qui vont être apportées à votre projet avant de les accepter. Cette opération s’effectue dans la fenêtre **Aperçu des modifications**.  Par exemple, voici une fenêtre **Aperçu des modifications** montrant ce qui sera modifié pendant une refactorisation de changement de nom dans un projet C# :

![Aperçu des modifications](media/previewchanges.png)

La moitié supérieure de la fenêtre affiche les lignes spécifiques qui seront modifiées, chacune avec une case à cocher. Vous pouvez cocher ou décocher chaque case si vous souhaitez appliquer de manière sélective la refactorisation uniquement à des lignes spécifiques.

La moitié inférieure de la fenêtre présente le code mis en forme du projet qui sera modifié, avec les zones affectées mises en surbrillance. Quand vous sélectionnez la ligne spécifique dans la partie supérieure de la fenêtre, la ligne correspondante dans la partie inférieure est mise en surbrillance. Cela vous permet d’accéder rapidement à la ligne appropriée et de voir le code environnant.

Après avoir vérifié les modifications, cliquez sur le bouton **Appliquer** pour valider ces modifications, ou cliquez sur le bouton **Annuler** pour laisser les choses telles qu’elles étaient.

## <a name="see-also"></a>Voir aussi

- [Refactorisation dans Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Actions rapides](../ide/quick-actions.md)
