---
title: Général, débogage, boîte de dialogue Options | Microsoft Docs
ms.date: 11/12/2019
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 528fa04b081937af69e647b01911ed00c1ec40c9
ms.sourcegitcommit: 9801fc66a14c0f855b9ff601fb981a9e5321819e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74072714"
---
# <a name="general-debugging-options"></a>Options de débogage générales

Pour définir les options du débogueur Visual Studio, sélectionnez **outils** > **options**, puis sous **débogage** , activez ou désactivez les cases à cocher en regard des options **générales** . Vous pouvez restaurer tous les paramètres par défaut à l’aide des **outils** > **paramètres d’importation et d’exportation** > **Réinitialiser tous les paramètres**. Pour réinitialiser un sous-ensemble de paramètres, enregistrez vos paramètres à l’aide de l' **Assistant importation et exportation de paramètres** avant d’effectuer les modifications que vous souhaitez tester, puis importez vos paramètres enregistrés ultérieurement.

Vous pouvez définir les options **générales** suivantes :

**Demander avant de supprimer tous les points d’arrêt**: requiert une confirmation avant d’exécuter la commande **Supprimer tous les points d’arrêt** .

**Arrêter tous les processus lorsqu’un processus s’arrête**: arrête simultanément tous les processus auxquels le débogueur est attaché, lorsqu’un arrêt se produit.

Arrêter lorsque des exceptions dépassent les **limites AppDomain ou managées/natives**: dans le cadre du débogage managé ou en mode mixte, le Common Language Runtime peut intercepter les exceptions qui franchissent les limites entre les domaines d’application ou les limites managées/natives quand les éléments suivants les conditions sont vraies :

1. Lorsque le code natif appelle le code managé à l'aide de COM Interop et que le code managé lève une exception. Consultez [Introduction à COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quand le code managé s’exécutant dans le domaine d’application 1 appelle du code managé dans le domaine d’application 2 et que le code dans le domaine d’application 2 lève une exception. Consultez [Programmation avec des domaines d’application](/dotnet/articles/framework/app-domains/index).

3. Lorsque le code appelle une fonction à l’aide de la réflexion, et que cette fonction lève une exception. Consultez [réflexion](/dotnet/framework/reflection-and-codedom/reflection).

Dans les conditions 2 et 3, l’exception est parfois interceptée par du code managé dans `mscorlib` plutôt que par le common language runtime. Cette option n'a aucune incidence sur l'arrêt sur les exceptions interceptées par `mscorlib`.

**Activer le débogage au niveau**de l’adresse : active les fonctionnalités avancées pour le débogage au niveau de l’adresse (la fenêtre **code machine** , la fenêtre **registres** et les points d’arrêt sur adresse).

- **Afficher le code machine si la source n’est pas disponible**: affiche automatiquement la fenêtre code **machine** lorsque vous déboguez du code pour lequel la source n’est pas disponible.

**Activer les filtres de point d’arrêt**: vous permet de définir des filtres sur les points d’arrêt afin qu’ils affectent uniquement des processus, threads ou ordinateurs spécifiques.

**Utiliser la nouvelle assistance d’exception**: active l’assistance d’exception qui remplace l’Assistant Exception. (Le programme d’assistance d’exception est pris en charge à partir de Visual Studio 2017)

> [!NOTE]
> Pour le code managé, cette option était précédemment appelée **activer l’Assistant Exception** .

**Activer uniquement mon code**: le débogueur affiche et exécute un pas à pas détaillé dans le code utilisateur (« mon code ») uniquement, en ignorant le code système et tout autre code optimisé ou qui n’a pas de symboles de débogage.

- **Avertir s’il n’y a pas de code utilisateur au lancement (managé uniquement)** : quand le débogage commence par uniquement mon code activé, cette option vous avertit s’il n’y a pas de code utilisateur (« mon code »).

**Activer l’exécution pas à pas de la source .NET Framework**: permet au débogueur d’effectuer un pas à pas détaillé dans .NET Framework source. L’activation de cette option désactive automatiquement Uniquement mon code. Les symboles de .NET Framework sont téléchargés vers un emplacement du cache. Modifiez l’emplacement du cache à l’aide de la boîte de dialogue **options** , catégorie **débogage** , page **symboles** .

**Pas à pas principal dans les propriétés et les opérateurs (managé uniquement)** : empêche le débogueur d’effectuer un pas à pas détaillé dans les propriétés et les opérateurs dans le code managé.

**Activer l’évaluation de la propriété et d’autres appels de fonction implicite**: active l’évaluation automatique des propriétés et des appels de fonction implicite dans les fenêtres de variables et la boîte de dialogue **Espion express** .

- **Appeler une fonction de conversion de chaînes sur des objetsC# dans des fenêtres de variables (et JavaScript uniquement)** : exécute un appel de conversion de chaîne implicite lors de l’évaluation d’objets dans les fenêtres de variables. Le résultat est affiché sous la forme d’une chaîne et non du nom de type. S'applique uniquement lors du débogage en code C#. Ce paramètre peut être substitué par l’attribut DebuggerDisplay (consultez [utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Activer la prise en charge du serveur source**: indique au débogueur Visual Studio d’extraire les fichiers sources des serveurs sources qui implémentent le protocole SrcSrv (`srcsrv.dll`). Team Foundation Server et les outils de débogage pour Windows sont deux serveurs sources qui implémentent le protocole. Pour plus d’informations sur le programme d’installation de SrcSrv, consultez la documentation de [SRCSRV](/windows-hardware/drivers/debugger/srcsrv) . En outre, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> La lecture des fichiers *.pdb* pouvant exécuter du code arbitraire dans les fichiers, vérifiez que le serveur possède un niveau de confiance suffisant.

- **Imprimer les messages de diagnostic du serveur source dans la fenêtre Sortie**: lorsque la prise en charge du serveur source est activée, ce paramètre active l’affichage du diagnostic.

- **Autoriser le serveur source pour les assemblys de confiance partielle (managé uniquement)** : lorsque la prise en charge du serveur source est activée, ce paramètre remplace le comportement par défaut qui consiste à ne pas récupérer les sources des assemblys de confiance partielle.

- **Toujours exécuter les commandes de serveur source non fiables sans invite**: lorsque la prise en charge du serveur source est activée, ce paramètre remplace le comportement par défaut de l’invite lors de l’exécution d’une commande non approuvée.

**Activer la prise en charge du lien source**: indique au débogueur Visual Studio de télécharger les fichiers sources des fichiers *. pdb* qui contiennent les informations de lien source. Pour plus d’informations sur le lien source, consultez la [spécification du lien source](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Le lien source téléchargeant les fichiers à l’aide du protocole http ou HTTPS, assurez-vous que vous faites confiance au fichier *. pdb* .

- **Revenir à git Credential Manager Authentication pour toutes les demandes de lien source**: lorsque la prise en charge du lien source est activée et qu’une demande de lien source échoue pour l’authentification, Visual Studio appelle le gestionnaire d’informations d’identification git.

**Mettre en surbrillance la ligne entière pourC++ les points d’arrêt et l’instruction actuelle (uniquement)** : quand le débogueur met en surbrillance un point d’arrêt ou une instruction actuelle, il met en surbrillance la ligne entière

Les **fichiers sources doivent correspondre exactement à la version d’origine**: indique au débogueur de vérifier qu’un fichier source correspond à la version du code source utilisée pour générer le fichier exécutable que vous déboguez. Si la version ne correspond pas, vous êtes invité à rechercher une source correspondante. Si aucune source correspondante n'est trouvée, le code source n'est pas affiché pendant le débogage.

**Rediriger tout le texte de la fenêtre sortie vers la fenêtre exécution**: envoie tous les messages du débogueur qui s’affichent normalement dans la fenêtre **sortie** vers la fenêtre **exécution** à la place.

**Afficher la structure brute des objets dans les fenêtres de variables**: désactive toutes les personnalisations d’affichage de la structure des objets. Pour plus d’informations sur les personnalisations d’affichage, consultez [créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-managed-objects.md).

**Supprimer l’optimisation JIT lors du chargement du module (managé uniquement)** : désactive l’optimisation JIT du code managé lorsqu’un module est chargé et que JIT est compilé pendant que le débogueur est attaché. La désactivation de l'optimisation peut simplifier le débogage de certains problèmes, mais elle se fait au détriment des performances. Si vous utilisez Uniquement mon code, la suppression de l'optimisation JIT peut entraîner l'affichage du code non-utilisateur comme du code utilisateur (« Mon code »). Pour plus d’informations, consultez [optimisation et débogage JIT](../debugger/jit-optimization-and-debugging.md).

**Activer le débogage JavaScript pour ASP.net (chrome, Microsoft Edge et IE)** : active le débogueur de script pour les applications ASP.net. Lors de la première utilisation dans Chrome, vous devrez peut-être vous connecter au navigateur pour activer les extensions chrome que vous avez installées. Désactivez cette option pour rétablir le comportement hérité.

**Activer les outils de développement Edge pour les applications JavaScript UWP (expérimental)** : active les outils de développement pour les applications JavaScript UWP dans Microsoft Edge.

**Activer le débogueur JavaScript chrome hérité pour ASP.net**: active le débogueur de script JavaScript chrome hérité pour les applications ASP.net. Lors de la première utilisation dans Chrome, vous devrez peut-être vous connecter au navigateur pour activer les extensions chrome que vous avez installées.

**Utilisez la méthode expérimentale pour lancer le débogage JavaScript chrome lors de l’exécution de Visual Studio en tant qu’administrateur**: indique à Visual Studio d’essayer une nouvelle façon de lancer chrome pendant le débogage JavaScript.

**Charger les exportations de dll (natif uniquement)** : charge les tables d’exportation de dll. Les informations symboliques de tables d’exportation de dll peuvent être utiles si vous utilisez des messages Windows, des procédures Windows (WindowProcs), des objets COM, le marshaling ou toute dll pour laquelle vous n’avez pas de symbole. La lecture des informations d’exportation des dll implique une certaine charge mémoire. Par conséquent, cette fonctionnalité est désactivée par défaut.

Pour savoir quels symboles sont disponibles dans la table d’exportation d’une dll, utilisez `dumpbin /exports`. Il existe des symboles pour toutes les dll système 32 bits. En lisant le résultat de `dumpbin /exports` , vous apprenez le nom exact de la fonction, y compris les caractères non alphanumériques. Cette information peut être utile pour définir un point d'arrêt sur une fonction. Les noms de fonctions provenant de tables d’exportation de dll peuvent s’afficher sous une forme tronquée dans les autres parties du débogueur. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours (la plus profondément imbriquée) apparaissant en tête de liste. Pour plus d'informations, consultez [dumpbin /exports](/cpp/build/reference/dash-exports).

**Afficher le diagramme ascendant des piles parallèles**: contrôle la direction dans laquelle les piles sont affichées dans la fenêtre **Piles parallèles** .

**Ignorer les exceptions d’accès à la mémoire GPU si les données écrites n’ont pas modifié la valeur**: ignore les conditions de concurrence qui ont été détectées pendant le débogage si les données n’ont pas changé. Pour plus d’informations, consultez [débogage du code GPU](../debugger/debugging-gpu-code.md).

**Utiliser le mode de compatibilité managée**: remplace le moteur de débogage par défaut par une version héritée pour activer les scénarios suivants :

- Vous utilisez un langage .NET autre que C#, Visual Basic ou F# qui fournit son propre évaluateur d’expression (cela inclut C++/CLI).

- Vous souhaitez activer modifier & Continuer pour les C++ projets pendant le débogage en mode mixte.

> [!NOTE]
> Le choix du mode de compatibilité managé désactive certaines fonctionnalités qui sont implémentées uniquement dans le moteur de débogage par défaut. Le moteur de débogage hérité a été remplacé dans Visual Studio 2012.

**Utiliser les évaluateurs d’expression C# hérités et VB**: le débogueur utilise les évaluateurs d’expression Visual Studio 2013 C# ou Visual Basic plutôt que les évaluateurs d’expression Roslyn Visual Studio 2015.

**Avertir lors de l’utilisation de visualiseurs de débogueur personnalisés sur des processus potentiellement dangereux (managé uniquement)** : Visual Studio vous avertit quand vous utilisez un visualiseur de débogueur personnalisé qui exécute du code dans le processus débogué, car il peut s’agir d’un code non sécurisé. .

**Activer l’allocateur de tas de débogage Windows (natif uniquement)** : active le tas de débogage Windows pour améliorer les diagnostics de tas. L’activation de cette option affecte les performances de débogage.

**Activer les outils de débogage de l’interface utilisateur pour XAML**: l’arborescence d’éléments visuels dynamique et la propriété Active Explorer Windows s’affichent lorsque vous démarrez le débogage (**F5**) un type de projet pris en charge. Pour plus d’informations, consultez [inspecter les propriétés XAML pendant le débogage](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Aperçu des éléments sélectionnés dans l’arborescence d’éléments visuels dynamique**: l’élément XAML dont le contexte est sélectionné est également sélectionné dans la fenêtre de l’arborescence d’éléments **visuels dynamique** .

- **Afficher les outils d’exécution dans l’application**: affiche les commandes de l’arborescence d’éléments **visuels en direct** dans une barre d’outils de la fenêtre principale de l’application XAML en cours de débogage. Cette option a été introduite dans Visual Studio 2015 Update 2.

- **Activer le rechargement à chaud XAML**: vous permet d’utiliser la fonctionnalité de rechargement à chaud XAML avec du code XAML lorsque votre application est en cours d’exécution. (Cette fonctionnalité était précédemment appelée « modifier et continuer XAML »)

::: moniker range=">= vs-2019" 
- **Activer uniquement mon code XAML**: à partir de Visual Studio 2019 version 16,4, l’arborescence d’éléments **visuels en direct** affiche par défaut uniquement le code XAML classé comme code utilisateur. Si vous désactivez cette option, tous les codes XAML générés sont affichés dans l’outil.

- **Désactiver le mode de sélection lorsqu’un élément est sélectionné** À compter de Visual Studio 2019 version 16,4, le bouton du sélecteur d’éléments de la barre d’outils dans l’application (**activer la sélection**) est désactivé lorsqu’un élément est sélectionné. Si vous désactivez cette option, la sélection des éléments reste activée jusqu’à ce que vous cliquiez à nouveau sur le bouton de la barre d’outils dans l’application.
::: moniker-end

**Activer outils de diagnostic lors du débogage**: la fenêtre de **outils de diagnostic** s’affiche pendant le débogage.

**Afficher le temps écoulé perftip durant pendant le débogage**: la fenêtre de code affiche le temps écoulé d’un appel de méthode donné lors du débogage.

**Activer modifier & continuer**: active la fonctionnalité Modifier & continuer pendant le débogage.

- **Activer modifier & continuer natif**: vous pouvez utiliser la fonctionnalité Modifier & Continuer lors du débogage de C++ code natif. Pour plus d’informations, consultez [modifier & continuerC++()](../debugger/edit-and-continue-visual-cpp.md).

- **Appliquer les modifications à la poursuite du traitement (natif uniquement)** : Visual Studio compile et applique automatiquement toutes les modifications de code en suspens que vous avez apportées lorsque vous poursuivez le processus à partir d’un état d’arrêt. Si cette option n’est pas sélectionnée, vous pouvez choisir d’appliquer les modifications à l’aide de l’élément **Appliquer les modifications du code** dans le menu **Déboguer**.

- **Signaler le code périmé (natif uniquement)** : obtenir des avertissements sur le code périmé.

**Afficher le bouton Exécuter jusqu’au clic dans l’éditeur pendant le débogage**: lorsque cette option est sélectionnée, le bouton [Exécuter jusqu’au clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) s’affiche pendant le débogage.

**Fermer automatiquement la console quand le débogage s’arrête**: indique à Visual Studio de fermer la console à la fin d’une session de débogage.

::: moniker range=">= vs-2019"
**Activer l’évaluation rapide des expressions (managé uniquement)** : permet au débogueur de tenter une évaluation plus rapide en simulant l’exécution de propriétés et de méthodes simples.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Options disponibles dans les versions antérieures de Visual Studio

Si vous utilisez une version antérieure de Visual Studio, certaines options supplémentaires peuvent être présentes.

**Activez l’Assistant Exception**: pour le code managé, active l’Assistant Exception. À compter de Visual Studio 2017, le programme d’assistance de l’exception a remplacé l’Assistant Exception.

**Dérouler la pile des appels sur les exceptions non gérées**: force la fenêtre **pile des appels** à restaurer la pile des appels au point qui précède l’exception non gérée.

**Avertir s’il n’y a aucun symbole au lancement (natif uniquement)** : affiche une boîte de dialogue d’avertissement lorsque vous déboguez un programme pour lequel le débogueur n’a pas d’informations de symbole.

**Avertir si le débogage de script est désactivé au lancement**: affiche une boîte de dialogue d’avertissement lorsque le débogueur est lancé avec le débogage de script désactivé.

**Utiliser le mode de compatibilité natif**: quand cette option est sélectionnée, le débogueur utilise le débogueur natif Visual Studio 2010 au lieu du nouveau débogueur natif.

- Utilisez cette option lorsque vous déboguez du code C++ .net, car le nouveau moteur de débogage ne prend pas en charge C++ l’évaluation des expressions .net. Toutefois, l’activation du mode de compatibilité natif désactive de nombreuses fonctionnalités qui dépendent de l’implémentation du débogueur actuel pour fonctionner. Par exemple, le moteur hérité ne dispose pas de nombreux visualiseurs pour les types intégrés comme `std::string` dans les projets Visual Studio 2015.   Utilisez des projets Visual Studio 2013 pour une expérience de débogage optimale dans ces cas.

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
