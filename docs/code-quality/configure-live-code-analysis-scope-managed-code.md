---
title: Configurer l’étendue de l’analyse du code en temps réel pour .NET
ms.date: 09/01/2020
description: En savoir plus sur l’analyse en arrière-plan dans Visual Studio. Consultez Comment limiter l’analyse au document visible, à tous les documents ouverts ou à tous les fichiers et projets.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7a6a7253d4104fbcde09b96b86f5f83a864677cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860397"
---
# <a name="configure-live-code-analysis-for-net"></a>Configurer l’analyse du code en temps réel pour .NET

Visual Studio exécute une série d’analyses de code en direct, également appelées *analyse d’arrière-plan*, pendant que vous modifiez des fichiers sources dans l’éditeur. Une analyse minimale est nécessaire pour une expérience de modification de l’IDE de Visual Studio acceptable. Certaines d’entre elles sont destinées à améliorer la réactivité des fonctionnalités de l’IDE. Bien qu’il s’agit d’activer des fonctionnalités IDE supplémentaires, telles que les diagnostics et les correctifs de code des analyseurs Roslyn. Selon les fonctionnalités, ces analyses peuvent être regroupées comme suit :

- **Calcul en arrière-plan des diagnostics**: analyse pour calculer les erreurs, les avertissements et les suggestions dans les fichiers sources. Ces diagnostics s’affichent sous la forme d’entrées dans la liste d’erreurs et de tildes dans l’éditeur. Elles peuvent être classées en deux catégories :
  - Diagnostics du compilateur C# et Visual Basic
  - Diagnostics de l’analyseur Roslyn, notamment :

    - Analyseurs IDE intégrés pour les suggestions de style de code
    - Analyseurs de l’autorité de certification intégrés pour les suggestions de qualité du code
    - Packages de l’analyseur tiers [installés](./install-roslyn-analyzers.md) pour les projets de la solution actuelle.

- **Autres analyses en arrière-plan**: analyse pour améliorer la réactivité et l’interaction de Visual Studio pour les fonctionnalités IDE. Voici quelques exemples de ces analyses :
  - Analyse en arrière-plan des fichiers ouverts.
  - Compilation en arrière-plan de projets avec des fichiers ouverts pour réaliser des symboles afin d’améliorer la réactivité de certaines fonctionnalités de l’IDE.
  - Génération de la syntaxe et des caches de symboles.
  - Détection de l’Association de concepteur pour les fichiers sources, tels que les formulaires, les contrôles, etc.

## <a name="default-analysis-scope"></a>Étendue de l’analyse par défaut

Par défaut, l’analyse du code en temps réel pour le calcul en arrière-plan des Diagnostics s’exécute pour tous les fichiers _ouverts_ dans Visual Studio. Quelques-unes des _autres analyses en arrière-plan_ mentionnées ci-dessus s’exécutent pour tous les projets, qui ont au moins un fichier ouvert. Tandis que peu d’analyses en arrière-plan s’exécutent pour l’ensemble de la solution.

## <a name="custom-analysis-scope"></a>Étendue de l’analyse personnalisée

L’étendue par défaut de chaque analyse en arrière-plan a été optimisée pour l’expérience utilisateur optimale, les fonctionnalités et les performances pour la majorité des scénarios et solutions clients. Toutefois, dans certains cas, les clients peuvent souhaiter personnaliser cette étendue pour réduire ou augmenter l’analyse en arrière-plan. Par exemple :

- Mode économie d’énergie : si les utilisateurs s’exécutent sur une batterie d’ordinateurs portables, ils peuvent réduire la consommation d’énergie pour une durée de vie de batterie plus longue. Dans ce scénario, ils souhaitent réduire l’analyse en arrière-plan.
- Analyse du code à la demande : si les utilisateurs préfèrent désactiver l’exécution de l’analyseur en temps réel et exécuter manuellement l’analyse du code à la demande, ils souhaitent réduire l’analyse en arrière-plan. Consultez [Comment : exécuter manuellement l’analyse du code à la demande](./how-to-run-code-analysis-manually-for-managed-code.md).
- Analyse complète de la solution : si les utilisateurs souhaitent toujours voir tous les diagnostics dans tous les fichiers de la solution, qu’ils soient ouverts ou non dans l’éditeur. Dans ce scénario, ils souhaitent maximiser l’étendue de l’analyse en arrière-plan à la solution complète.

À compter de Visual Studio 2019 version 16,5, les utilisateurs peuvent personnaliser explicitement l’étendue de l’ensemble de l’analyse du code en direct, y compris le calcul des diagnostics, pour les projets C# et Visual Basic. Les étendues d’analyse disponibles sont les suivantes :

- **Document actif**: réduit l’étendue de l’analyse du code en temps réel pour qu’elle s’exécute uniquement pour le fichier actif ou visible dans l’éditeur.
- **Documents ouverts**: étendue de l’analyse du code en direct par défaut, comme décrit dans la section ci-dessus.
- **Solution complète**: optimise l’étendue de l’analyse du code en temps réel pour l’exécution de tous les fichiers et projets de l’ensemble de la solution.

Vous pouvez choisir l’une des étendues d’analyse personnalisées ci-dessus dans la boîte de dialogue Options des outils en suivant les étapes ci-dessous :

1. Pour ouvrir la boîte de dialogue **options** , dans la barre de menus de Visual Studio, choisissez **Outils**  >  **options**.

2. Dans la boîte de dialogue **options** , choisissez **éditeur de texte**  >  **C#** ou **Basic**  >  **avancé**.

3. Sélectionnez l' **étendue d’analyse en arrière-plan** souhaitée pour personnaliser l’étendue de l’analyse. Lorsque vous avez terminé, choisissez **OK** .

![Étendue de l’analyse.](./media/background-analysis-scope.png)

> [!NOTE]
> Avant Visual Studio 2019 version 16,5, les utilisateurs peuvent personnaliser l’étendue de l’analyse pour le calcul des diagnostics sur la totalité de la solution à l’aide de la case à cocher **activer l’analyse complète** de la solution dans **Outils**  >  **options**  >  **éditeur de texte**  >  **C#** ou   >  onglet **avancé** de base. Il n’existe aucune prise en charge pour réduire l’étendue de l’analyse en arrière-plan dans les versions antérieures de Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Réduire automatiquement l’étendue de l’analyse du code en direct

Si Visual Studio détecte que 200 Mo ou moins de mémoire système est disponible, il réduit automatiquement l’étendue de l’analyse du code en temps réel en « document actif ». Dans ce cas, une alerte s’affiche vous informant que Visual Studio a désactivé certaines fonctionnalités. Un bouton vous permet de revenir à l’étendue d’analyse précédente si vous le souhaitez.

![Texte d’alerte minimisant l’étendue de l’analyse](./media/fsa_alert.png)

## <a name="see-also"></a>Voir aussi

- [Suspension automatique de fonctionnalités](./automatic-feature-suspension.md)
- [Demande de fonctionnalité du mode d’économie d’énergie](https://github.com/dotnet/roslyn/issues/38429)
