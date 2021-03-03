---
title: Conseils pour améliorer les performances
description: Découvrez comment optimiser certaines fonctionnalités de Visual Studio que vous n’utilisez peut-être pas pour améliorer les performances.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e2187426fbd2e8892d41672c1cf682ed0b93592
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683770"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Conseils et astuces sur les performances dans Visual Studio

Les recommandations pour améliorer les performances de Visual Studio concernent les cas où la mémoire est insuffisante, ce qui se produit rarement. Dans ces situations, vous pouvez optimiser certaines fonctionnalités de Visual Studio que vous n’utilisez peut-être pas. Les conseils suivants ne sont pas à interpréter comme des recommandations générales.

> [!NOTE]
> Si vous rencontrez des difficultés à utiliser le produit en raison de problèmes de mémoire, faites-le nous savoir via [l’outil de commentaires](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Utiliser un système d’exploitation 64 bits

Si vous mettez à niveau votre système d’une version 32 bits de Windows vers une version 64 bits, vous passez de 2 Go à 4 Go la quantité de mémoire virtuelle disponible pour Visual Studio. Cela permet à Visual Studio de gérer des charges de travail beaucoup plus importantes, même avec un processus 32 bits.

Pour plus d’informations, consultez [Limites de mémoire](/windows/desktop/Memory/memory-limits-for-windows-releases) et [Use /LARGEADDRESSAWARE on 64-bit Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Désactiver la restauration automatique de fichiers

Visual Studio rouvre automatiquement les documents qui ont été laissés ouverts dans la session précédente. Cela peut prolonger la durée nécessaire au chargement d’une solution de 30 % ou plus, en fonction du type de projet et des documents en cours d’ouverture. Des concepteurs tels que Windows Forms et XAML, ainsi que certains fichiers JavaScript et typescript, peuvent être lents à ouvrir.

Visual Studio affiche un avertissement dans une barre jaune quand la restauration automatique de documents ralentit de manière significative le chargement d’une solution. Vous pouvez désactiver la réouverture automatique des fichiers en effectuant les étapes suivantes :

1. Sélectionnez **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** .

1. Dans la page **projets et solution**  >  **général** , désélectionnez **rouvrir les documents lors du chargement de la solution**.

Si vous désactivez la restauration automatique de fichiers, vous pouvez accéder rapidement aux fichiers à ouvrir, à l’aide de l’une des commandes [Atteindre](../ide/go-to.md) :

- Pour la fonctionnalité **Atteindre** générale, sélectionnez **Edition** > **Atteindre** > **Atteindre tout**, ou appuyez sur **Ctrl**+**T**.

- Accédez au dernier emplacement de modification d’une solution à l’aide de **modifier**  >  **atteindre pour**  >  **accéder à l’emplacement de la dernière modification** ou en appuyant sur **CTRL** + **Shift** + **RET**.

- Utilisez **Aller au fichier récent** pour afficher la liste des derniers fichiers ouverts dans une solution. Sélectionnez **modifier**  >  **atteindre** pour  >  **accéder au fichier récent** ou appuyez sur **CTRL** + **1**, **CTRL** + **R**.

## <a name="configure-debugging-options"></a>Configurer les options de débogage

En règle générale, si vous manquez de mémoire pendant le débogage des sessions, vous pouvez optimiser les performances en modifiant un peu la configuration.

- **Activer Uniquement mon code**

    L’optimisation la plus simple consiste à activer la fonctionnalité **Uniquement mon code**, qui charge uniquement des symboles pour votre projet. L’activation de cette fonctionnalité peut contribuer à économiser considérablement la mémoire pour le débogage des applications managées (.NET). Cette option est déjà activée par défaut dans certains types de projets.

    Pour activer **Uniquement mon code**, choisissez **Outils** > **Options** > **Débogage** > **Général**, puis sélectionnez **Activer Uniquement mon code**.

- **Spécifier les symboles à charger**

    Pour le débogage natif, le chargement des fichiers de symboles (*.pdb*) consomme beaucoup de ressources mémoire. Vous pouvez configurer les paramètres de symboles de votre débogueur pour économiser la mémoire. En règle générale, vous configurez la solution pour charger uniquement les modules de votre projet.

    Pour spécifier le chargement de symboles, choisissez **Outils**  >  **options** de  >  **débogage**  >  **symboles**.

    Définissez les options sur **Uniquement les modules spécifiés** au lieu de **Tous les modules**, puis spécifiez les modules que vous voulez charger. Pendant le débogage, vous pouvez également cliquer avec le bouton droit sur des modules spécifiques dans la fenêtre **Modules** pour inclure explicitement un module dans le chargement de symboles. (Pour ouvrir la fenêtre pendant le débogage, choisissez **Déboguer**  >  **Windows**  >  **Modules**.)

    Pour plus d’informations, consultez [Présentation des fichiers de symboles](?view=vs-2019&preserve-view=true).

- **Désactiver les outils de diagnostic**

    Nous vous recommandons de désactiver le profilage de l’UC après utilisation. Cette fonctionnalité peut consommer de grandes quantités de ressources. Une fois que le profilage de l’UC est activé, cet état est conservé dans les sessions de débogage suivantes, il est donc recommandé de le désactiver explicitement une fois terminé. Vous pouvez économiser des ressources en désactivant les outils de diagnostic pendant le débogage si vous n’avez pas besoin des fonctionnalités fournies.

    Pour désactiver l' **outils de diagnostic**, démarrez une session de débogage, sélectionnez **Outils**  >  **options**  >  **débogage**  >  **général**, puis désactivez l’option **activer le outils de diagnostic en cours de débogage** .

    Pour plus d’informations, consultez [Outils de profilage](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Désactiver des outils et des extensions

Certains outils ou extensions peuvent être désactivés pour améliorer les performances.

> [!TIP]
> Vous pouvez souvent isoler les problèmes de performances en désactivant une par une les extensions et en revérifiant les performances.

### <a name="managed-language-service-roslyn"></a>Service de langage géré (Roslyn)

Pour plus d’informations sur les performances de .NET Compiler Platform (« Roslyn »), consultez [Performance considerations for large solutions](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

- **Désactiver l’analyse complète de la solution**

    Visual Studio analyse l’ensemble de votre solution afin d’offrir une expérience complète sur les erreurs avant d’appeler une génération. Cette fonctionnalité est utile pour identifier les erreurs dès que possible. Toutefois, pour les solutions volumineuses, cette fonctionnalité peut consommer des ressources de mémoire considérables. Si vous rencontrez des problèmes de mémoire ou du même type, vous pouvez désactiver cette expérience pour libérer ces ressources. Par défaut, cette option est activée pour Visual Basic et désactivée pour C#.

    Pour désactiver **Analyse complète de la solution**, choisissez **Outils** > **Options** > **Éditeur de texte**, puis sélectionnez **Visual Basic** ou **C#**. Choisissez **Avancé** et décochez la case **Activer l’analyse complète de la solution**.

- **Désactiver CodeLens**

    Visual Studio effectue une tâche **Rechercher toutes les références** sur chaque méthode qui s’affiche. CodeLens fournit des fonctionnalités comme l’affichage en ligne du nombre de références. Le travail est exécuté dans un processus distinct, tel que *ServiceHub.RoslynCodeAnalysisService32*. Dans les solutions volumineuses ou sur des systèmes limités en ressources, cette fonctionnalité peut avoir un impact significatif sur les performances. Si vous rencontrez des problèmes de mémoire (par exemple quand vous chargez une solution volumineuse sur un ordinateur de 4 Go) ou si ce processus utilise l’UC de manière intensive, vous pouvez désactiver CodeLens afin de libérer des ressources.

    Pour désactiver **CodeLens**, choisissez **Outils** > **Options** > **Éditeur de texte** > **Tous les langages** > **CodeLens** et désélectionnez la fonctionnalité.

    > [!NOTE]
    > CodeLens est disponible dans les éditions Professional et Enterprise de Visual Studio.

### <a name="other-tools-and-extensions"></a>Autres outils et extensions

- **Désactiver les extensions**

    Les extensions sont des composants logiciels supplémentaires ajoutés à Visual Studio qui fournissent de nouvelles fonctionnalités ou étendent les fonctionnalités existantes. Les extensions peuvent souvent être une source de problèmes de ressources mémoire. Si vous rencontrez des problèmes de ressources mémoire, essayez de désactiver les extensions une par une pour connaître leur impact sur le scénario ou le flux de travail.

   ::: moniker range="vs-2017"

    Pour désactiver des extensions, accédez à **Outils** > **Extensions et mises à jour** et désactivez une extension particulière.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Pour désactiver des extensions, accédez à **Outils** > **Gérer les extensions** et désactivez une extension particulière.

   ::: moniker-end

- **Désactiver le mode carte**

    Le [**mode carte**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) affiche des lignes de code, en miniature, sur la barre de défilement. Le mode mappage est activé par défaut.

    Pour désactiver le mode carte, accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **tous les langages**  >  **barres de défilement**, puis, dans la section **comportement** , désactivez l’option **utiliser le mode mappage pour la barre de défilement verticale** .

- **Désactiver le retour automatique à la ligne**

    [**Retour**](./reference/how-to-manage-word-wrap-in-the-editor.md) automatique à la ligne affiche la partie d’une longue ligne de code qui s’étend au-delà de la largeur actuelle de la fenêtre de l’éditeur de code. Le retour automatique à la ligne est activé par défaut.

    Pour désactiver le retour automatique à la ligne pour un projet sur lequel vous travaillez actuellement, accédez à **modifier** le retour automatique à  >    >  **la ligne**. (Vous pouvez activer ou désactiver ce paramètre à l’aide des mêmes commandes de menu.)

    Pour désactiver le retour automatique à la ligne pour tous les projets, accédez à **Outils**  >  **options**  >    >  **éditeur de texte** général  >  **tous les langages**  >  **général**, puis, dans la section **paramètres** , désélectionnez l’option retour automatique à la **ligne** .

- **Désactiver le concepteur XAML**

    Le concepteur XAML est activé par défaut, mais consomme des ressources seulement si vous ouvrez un fichier *.xaml*. Si vous utilisez des fichiers XAML, mais ne voulez pas utiliser les fonctionnalités du concepteur, désactivez cette fonctionnalité pour libérer de la mémoire.

    Pour désactiver concepteur XAML, accédez à **Outils**  >  **options**  >  **Concepteur XAML**  >  **activer concepteur XAML**, puis désélectionnez l’option.

- **Supprimer des charges de travail**

    Vous pouvez utiliser Visual Studio Installer pour supprimer des charges de travail qui ne sont plus utilisées. Cette action permet de rationaliser le coût du démarrage et de l’exécution en ignorant les packages et les assemblys qui ne sont plus nécessaires.

- **Ajouter des fichiers non suivis à local. gitignore**

    Visual Studio exécute la commande git `git status` avec des fichiers non suivis pour fournir une expérience transparente lorsque vous ajoutez de nouveaux fichiers à un référentiel. Lorsqu’il y a un grand nombre de fichiers non suivis, `git status` peut consommer de la mémoire supplémentaire. Pour ignorer ces fichiers et améliorer les performances de `git status` , vous pouvez ajouter ces fichiers ou dossiers à votre fichier local. gitignore. Pour accéder au fichier, accédez à **git**  >  **paramètres**  >  **référentiel git paramètres**. Ensuite, dans la section **fichiers git** , cliquez sur **Ajouter** pour créer un fichier. gitignore ou sur **modifier** si vous en avez déjà un.

## <a name="force-a-garbage-collection"></a>Forcer une opération de garbage collection

Le CLR utilise un système de gestion de mémoire garbage collection. Dans ce système, la mémoire est parfois utilisée par des objets qui ne sont plus nécessaires. Cet état est temporaire. Le récupérateur de mémoire libère cette mémoire en fonction de ses méthodes heuristiques en matière d’utilisation des ressources et de performances. Vous pouvez obliger le CLR à collecter la mémoire inutilisée à l’aide d’un raccourci clavier dans Visual Studio. Si une quantité importante de mémoire est en attente de nettoyage et que vous forcez une opération de garbage collection, vous devez voir chuter l’utilisation de la mémoire par le processus *devenv.exe* dans le **Gestionnaire des tâches**. Cette méthode est rarement nécessaire. Toutefois, quand une opération ayant consommé beaucoup de ressources se termine (par exemple, une génération complète, une session de débogage ou un événement d’ouverture de solution), elle peut vous aider à déterminer la quantité de mémoire qui est réellement utilisée par le processus. Parce que Visual Studio est mixte (à la fois managé et natif), il est parfois possible que l’allocateur natif et le récupérateur de mémoire entrent en concurrence pour utiliser des ressources mémoire limitées. Dans les situations d’utilisation importante de la mémoire, il peut être utile de forcer l’exécution du récupérateur de mémoire.

Pour forcer un garbage collection, utilisez la touche d’opération suivante : **CTRL** + **ALT** + **MAJ** + **F12**, **CTRL** + **ALT** + **MAJ** + **F12** (appuyez deux fois).

Si le forçage de l’opération de garbage collection permet à votre scénario de fonctionner de manière fiable, envoyez un rapport à travers l’outil de commentaires de Visual Studio, car ce comportement est susceptible d’être un bogue.

Pour obtenir une description détaillée du récupérateur de mémoire CLR, consultez [Concepts fondamentaux de l’opération de garbage collection](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Voir aussi

- [Optimiser le niveau de performance de Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Charger des solutions plus rapidement (blog Visual Studio)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)