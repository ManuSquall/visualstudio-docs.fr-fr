---
title: Configurer la portée d’analyse de code en direct pour le code géré
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432237"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Comment : Configurer la portée d’analyse de code en direct pour le code géré

## <a name="what-is-live-code-analysis-for-managed-code"></a>Qu’est-ce que « Analyse de code en direct » pour le code géré ?
Visual Studio exécute un tas d’analyses de code en direct, également appelée *analyse de fond,* tandis que vous modifiez des fichiers sources dans l’éditeur. Une partie de celui-ci est nécessaire une analyse minimale pour une expérience acceptable d’édition Visual Studio IDE. Une partie est pour une meilleure réactivité pour les fonctionnalités IDE. Alors que certains d’entre elles sont d’activer des fonctionnalités IDE supplémentaires, telles que les diagnostics et les correctifs de code des analyseurs Roslyn. Sur la base de la fonctionnalité, ces analyses peuvent être regroupées comme suit :

- **Calcul de fond des diagnostics**: Analyse pour calculer les erreurs, les avertissements et les suggestions dans les fichiers sources. Ces diagnostics apparaissent comme des entrées dans la liste d’erreurs et comme des gribouillis dans l’éditeur. Ils peuvent être classés en deux catégories :
    - Diagnostics de compilateur de C et Visual Basic
    - Diagnostics d’analyseur roslyn, qui comprend :

        - Analyseurs IDE intégrés pour les suggestions de style de code et
        - Paquets d’analyseurs tiers [installés](./install-roslyn-analyzers.md) pour des projets dans la solution actuelle.

- **Autres analyses de fond**: Analyse pour améliorer la réactivité et l’interaction Visual Studio pour les fonctionnalités IDE. Voici quelques exemples de telles analyses :
    - Analyse de fond des fichiers ouverts.
    - Compilation de fond de projets avec des fichiers ouverts pour réaliser des symboles pour améliorer la réactivité de certaines fonctionnalités IDE.
    - Construire la syntaxe et les caches de symboles.
    - Détection de l’association de concepteur pour les fichiers sources, tels que les formulaires, les contrôles, etc.

## <a name="default-analysis-scope"></a>Portée d’analyse par défaut

Par défaut, l’analyse de code en direct pour le calcul de fond des diagnostics s’exécute pour tous les fichiers qui sont _ouverts_ dans Visual Studio. Peu _d’autres analyses_ de fond mentionnées ci-dessus exécutent pour tous les projets, qui ont au moins un fichier ouvert. Bien que peu d’analyses de fond s’exécutent pour l’ensemble de la solution.

## <a name="custom-analysis-scope"></a>Portée d’analyse personnalisée

La portée par défaut de chaque analyse de fond a été réglée pour l’expérience utilisateur optimale, la fonctionnalité et les performances pour la majorité des scénarios et solutions des clients. Cependant, il y a des cas où les clients peuvent vouloir personnaliser cette portée pour diminuer ou augmenter l’analyse de fond. Par exemple :

- Mode d’économie d’énergie : Si les utilisateurs fonctionnent sur la batterie de l’ordinateur portable, ils peuvent vouloir minimiser la consommation d’énergie pour une plus longue durée de vie de la batterie. Dans ce scénario, ils voudraient minimiser l’analyse des antécédents.
- Analyse de code à la demande : Si les utilisateurs préfèrent désactiver l’exécution d’analyseur en direct et exécuter manuellement l’analyse de code à la demande, ils voudraient minimiser l’analyse de fond. Voir [comment : Exécuter manuellement l’analyse de code à la demande](./how-to-run-code-analysis-manually-for-managed-code.md).
- Analyse complète des solutions : Si les utilisateurs veulent toujours voir tous les diagnostics dans tous les fichiers de la solution, qu’ils soient ouverts ou non dans l’éditeur. Dans ce scénario, ils voudraient maximiser la portée de l’analyse de fond à une solution complète.

À partir de Visual Studio 2019 version 16.5, les utilisateurs peuvent personnaliser explicitement la portée de toutes les analyses de code en direct, y compris le calcul des diagnostics, pour les projets C et Visual Basic. Les portées d’analyse disponibles sont les suivante :

- **Document actuel**: minimise la portée d’analyse de code en direct pour ne l’exécuter que pour le fichier actuel ou visible dans l’éditeur.
- **Documents ouverts**: Portée d’analyse de code en direct par défaut, telle que décrite dans la section ci-dessus.
- **Solution complète**: maximise la portée d’analyse de code en direct pour exécuter pour tous les fichiers et projets dans l’ensemble de la solution.

Vous pouvez choisir l’une des portées d’analyse personnalisée ci-dessus dans le dialogue Tools Options en suivant les étapes ci-dessous :

1. Pour ouvrir la boîte de dialogue **Options,** sur le menu bar de Visual Studio, choisissez **Tools** > **Options**.

2. Dans la boîte de dialogue **Options,** choisissez **Text Editor** > **CMD** ou **Basic** > **Advanced**.

3. Sélectionnez la **portée d’analyse de fond** souhaitée pour personnaliser la portée de l’analyse. Choisissez **OK** quand vous avez terminé.

![Portée d’analyse.](./media/background-analysis-scope.png)

> [!NOTE]
> Avant visual Studio 2019 version 16.5, les utilisateurs peuvent personnaliser la portée d’analyse pour le calcul des diagnostics à toute la solution à l’aide de la case à cocher **d’analyse** de solution complète Enable à partir de **Tools** > **Options** > **Text Editor** > **C OU** **Basic** > **Advanced** tab. Il n’y a pas de support pour minimiser la portée d’analyse de fond dans les versions visual Studio antérieures.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Minimisez automatiquement la portée de l’analyse du code en direct

Si Visual Studio détecte que 200 Mo ou moins de mémoire système est à sa disposition, il minimise automatiquement la portée d’analyse de code en direct à "Document actuel". Si cela se produit, une alerte apparaît vous informant que Visual Studio a désactivé certaines fonctionnalités. Un bouton vous permet de revenir à la portée d’analyse préalable si vous le souhaitez.

![Texte d’alerte minimisant la portée de l’analyse](./media/fsa_alert.png)

## <a name="see-also"></a>Voir aussi

- [Suspension automatique de fonctionnalités](./automatic-feature-suspension.md)
- [Demande de fonctionnalité de mode d’économie d’énergie](https://github.com/dotnet/roslyn/issues/38429)
