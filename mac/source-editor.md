---
title: Éditeur de code source
description: Utilisation de l’éditeur de code source dans Visual Studio pour Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: d1ea74b4893032252d04ebe5fe5e65ca1eedaeeb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68493228"
---
# <a name="source-editor"></a>Éditeur de code source

Un éditeur de code source fiable est essentiel pour l’écriture d’un code succinct et efficace. Visual Studio pour Mac fournit un éditeur de code source sophistiqué qui est au centre de vos interactions avec l’IDE. L’éditeur de code source offre les fonctionnalités dont vous avez besoin pour effectuer votre travail avec facilité, depuis les fonctionnalités de base comme la coloration syntaxique, les extraits de code et le pliage de code, jusqu’aux avantages de son intégration au compilateur Roslyn, comme la complétion du code IntelliSense entièrement fonctionnelle.

L’éditeur de code source de Visual Studio pour Mac permet une expérience dans la continuité avec toutes les fonctionnalités dans l’IDE, comme le débogage, la refactorisation et l’intégration de la gestion de versions.

Cet article présente quelques-unes des principales fonctionnalités de l’éditeur de code source et décrit la façon dont vous pouvez utiliser Visual Studio pour Mac pour être aussi productif que possible.

## <a name="the-source-editor-experience"></a>L’expérience de l’éditeur de code source

Afficher et se déplacer efficacement dans le code fait partie intégrante du flux de travail de développement. La façon exacte dont vous voulez afficher et gérer le code est une décision personnelle, qui varie selon les développeurs, et souvent selon les projets.

Visual Studio pour Mac offre de nombreuses fonctionnalités puissantes pour rendre le développement multiplateforme aussi accessible et pratique que possible. Les sections ci-dessous décrivent certaines de ces fonctionnalités.

## <a name="code-folding"></a>Pliage de code

Le pliage de code facilite la gestion des fichiers de code source volumineux en permettant aux développeurs d’afficher ou de masquer des sections entières de code, par exemple en utilisant des directives, du code réutilisable et des commentaires, ainsi que des instructions #region. Le pliage de code est désactivé par défaut dans Visual Studio pour Mac

Pour activer le pliage de code, accédez à **Visual Studio > Préférences > Éditeur de texte > Général > Pliage de code** :

![Options du pliage de code](media/source-neweditor-image1.png)

Ce menu comprend également l’option pour plier par défaut les instructions #region et les commentaires, pour afficher à la place du code un indicateur nommé.

Pour afficher ou masquer des sections, utilisez le widget d’affichage en regard du numéro de ligne :

![Afficher ou masquer des sections de code](media/source-neweditor-image2.png)

Vous pouvez également passer de l’affichage au masquage des plis (et inversement) en utilisant l’élément de menu **Afficher > Pliage > Activer/Désactiver les plis > Activer/Désactiver tous les plis** :

![Élément de menu Pliage](media/source-editor-image19.png)

Cet élément de menu peut également être utilisé pour activer ou désactiver le pliage de code.

## <a name="word-wrap"></a>Retour automatique à la ligne

Le retour automatique à la ligne peut vous aider à gérer l’espace quand vous travaillez sur des lignes de code longues ou avec un espace d’affichage limité. Le retour automatique à la ligne peut également garantir que votre vue du code contient la totalité du contenu de votre fichier source, même quand vous ouvrez des volets qui peuvent masquer votre affichage ou réduire la largeur de votre vue du code source. 

Le retour automatique à la ligne est désactivé par défaut, mais vous pouvez l’activer via **Préférences** dans Visual Studio pour Mac. 

Pour activer le retour automatique à la ligne, accédez à **Visual Studio > Préférences > Éditeur de texte > Nouvel éditeur > Retour automatique à la ligne** :

![Options du retour automatique à la ligne](media/source-neweditor-wordwrap1.png)

Quand le retour automatique à la ligne est activé, les lignes qui dépassent la largeur de la vue de l’éditeur de code source sont automatiquement renvoyées à la ligne suivante dans votre fichier source. Vous pouvez également activer une option qui affichera un glyphe visible en regard des lignes avec retour à la ligne. Ceci vous permet de faire la distinction entre les lignes qui ont fait l’objet d’un retour à la ligne automatique et celles auxquelles vous avez appliqué un retour à la ligne manuellement.

![Texte renvoyé à la ligne avec retour automatique à la ligne activé](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Règle

La règle de colonnes est pratique pour déterminer la longueur des lignes, en particulier quand vous travaillez dans une équipe qui suit des directives sur les longueurs des lignes. Pour activer ou désactiver la règle de colonne, accédez à **Visual Studio > Préférences > Éditeur de texte > Marqueurs et règles**, puis sélectionnez (ou désélectionnez) **Afficher la règle de colonne**, comme illustré dans l’image suivante :

![Boîte de dialogue Préférences avec « Afficher la règle de colonnes » en surbrillance](media/source-editor-image5.png)

 Celle-ci s’affiche sous la forme d’une ligne verticale gris clair dans l’éditeur de code source.

## <a name="highlight-identifier-references"></a>Mettre en évidence les références d’identificateur

Quand l’option «Mettre en évidence les références d’identificateur » est activée, vous pouvez sélectionner n’importe quel symbole dans le code source et l’éditeur de code source fournit un guide visuel vers toutes les autres références dans ce fichier. Pour activer cette option, accédez à **Visual Studio > Préférences > Éditeur de texte > Marqueurs et règles**, puis sélectionnez _Mettre en évidence les références d’identificateur_, comme illustré dans l’image suivante :

![Boîte de dialogue Préférences avec « Mettre en évidence les références d’identificateur » en surbrillance](media/source-editor-image6.png)

La couleur de la mise en évidence est également pratique pour indiquer que quelque chose fait l’objet d’une affectation ou qu’il est référencé. Si quelque chose fait l’objet d’une affectation, il est mis en évidence en rouge ; s’il est référencé, il est mis en évidence en bleu :

![Exemple illustrant la couleur de la mise en surbrillance](media/source-editor-image7.png)

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code (Visual Studio sur Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Mode Plan (Visual Studio sur Windows)](/visualstudio/ide/outlining)
