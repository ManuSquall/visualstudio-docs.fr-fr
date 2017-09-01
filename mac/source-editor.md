---
title: "Éditeur de code source"
description: "Utilisation de l’éditeur de code source dans Visual Studio pour Mac"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: aa7635cd2593b871128c0588110f0bfdad5a82ec
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="source-editor"></a>Éditeur de code source

Un éditeur de code source fiable est essentiel pour l’écriture d’un code succinct et efficace. Visual Studio pour Mac fournit un éditeur de code source sophistiqué qui est au centre de vos interactions avec l’IDE. L’éditeur de code source offre les fonctionnalités dont vous avez besoin pour effectuer votre travail avec facilité, depuis les fonctionnalités de base comme la coloration syntaxique, les extraits de code et le pliage de code, jusqu’aux avantages de son intégration au compilateur Roslyn, comme la complétion du code IntelliSense entièrement fonctionnelle.

L’éditeur de code source de Visual Studio pour Mac permet une expérience dans la continuité avec toutes les fonctionnalités fournies par l’IDE, comme le débogage, la refactorisation et l’intégration de la gestion de versions.

Cette rubrique présente quelques-unes des principales fonctionnalités de l’éditeur de code source et décrit la façon dont vous pouvez utiliser Visual Studio pour Mac pour être aussi productif que possible.

## <a name="the-source-editor-experience"></a>L’expérience de l’éditeur de code source

Afficher et se déplacer efficacement dans le code fait partie intégrante du flux de travail de développement. La façon exacte dont vous voulez afficher et gérer le code est une décision personnelle, qui varie selon les développeurs, et souvent selon les projets.

Visual Studio pour Mac offre de nombreuses fonctionnalités puissantes pour rendre le développement multiplateforme aussi accessible et pratique que possible. Les sections ci-dessous décrivent certaines de ces fonctionnalités.


### <a name="code-folding"></a>Pliage de code

Le pliage de code facilite la gestion des fichiers de code source volumineux en permettant aux développeurs d’afficher ou de masquer des sections entières de code, par exemple en utilisant des directives, du code réutilisable et des commentaires, ainsi que des instructions #region. Cette fonctionnalité est désactivée par défaut dans Visual Studio pour Mac.

Pour activer le pliage de code, accédez à **Visual Studio > Préférences... > Éditeur de texte > Général > Pliage de code** :

![Options du pliage de code](media/source-editor-image1.png)

En plus de fournir la possibilité d’activer le pliage de code, ce menu comprend également l’option pour plier par défaut les instructions #region et les commentaires, pour afficher à la place du code un indicateur nommé.

Pour afficher ou masquer des sections, utilisez le widget d’affichage en regard du numéro de ligne :

 ![Afficher ou masquer des sections de code](media/source-editor-image2.png)

Vous pouvez également basculer entre l’affichage et le masquage des plis en utilisant l’élément de menu **Afficher > Pliage > Activer/Désactiver les plis > Activer/Désactiver tous les plis** :

 ![Élément de menu Pliage](media/source-editor-image19.png)

Cet élément de menu peut également être utilisé pour activer ou désactiver le pliage de code.

### <a name="white-space"></a>Espace blanc

Il peut être nécessaire d’afficher les caractères invisibles dans le code source. C’est un moyen visuel de vérifier que vous respectez les standards de codage et que vous n’utilisez pas de l’espace inutilement. C’est également très utile lors de l’écriture de code F#, dont l’évaluation dépend de l’indentation précise des lignes.

Définissez les options pour afficher les espaces en accédant à **Visual Studio > Préférences > Éditeur de texte > Marqueurs et règles**, comme illustré ci-dessous. Cette option permet de définir _quand_ les caractères invisibles sont affichés : Jamais, Dans la sélection ou Toujours :

 ![Options d’affichage des caractères invisibles](media/source-editor-image3.png)

Une option pour afficher les tabulations, les espaces et les fins de ligne est également disponible :

 ![Afficher les tabulations et les espaces](media/source-editor-image4.png)

 Les caractères invisibles sont affichés sous forme de points gris, comme illustré ci-dessous :

 ![espace affiché](media/source-editor-image22.png)


### <a name="ruler"></a>Règle

Afficher la règle de colonnes est pratique pour déterminer la longueur des lignes, en particulier quand vous travaillez dans une équipe qui suit des directives sur les longueurs des lignes. La règle de colonnes peut être activée ou désactivée en accédant à **Visual Studio > Préférences... > Éditeur de texte > Marqueurs et règles** et sélectionnez (ou désélectionnez) **Afficher la règle de colonnes**, comme illustré ci-dessous :

 ![](media/source-editor-image5.png)

 Celle-ci s’affiche sous la forme d’une ligne verticale gris clair dans l’éditeur de code source.


### <a name="highlight-identifier-references"></a>Mettre en évidence les références d’identificateur

Quand cette option est activée, un développeur peut placer le curseur de la souris sur n’importe quel symbole dans le code source : l’éditeur de code source fournit alors un guide visuel vers toutes les autres références dans ce fichier. Cette option est activée en accédant à **Visual Studio > Préférences... > Éditeur de texte > Marqueurs et règles** et en sélectionnant _Mettre en évidence les références d’identificateur_, comme illustré ci-dessous :

![](media/source-editor-image6.png)

La couleur de la mise en évidence est également pratique pour indiquer que quelque chose fait l’objet d’une affectation ou qu’il est référencé. Si quelque chose fait l’objet d’une affectation, il est mis en évidence en rouge ; s’il est référencé, il est mis en évidence en bleu :

![](media/source-editor-image7.png)




