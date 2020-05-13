---
title: Général, Debugging, Options Dialog Box (fr) Microsoft Docs
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472699"
---
# <a name="general-debugging-options"></a>Options de débogage général

Pour définir les options de débâcher Visual Studio, sélectionnez > des options **d’outils,** et sous**Options** **Debugging** sélectionnez ou désélectionner les cases à côté des options **générales.** Vous pouvez restaurer tous les paramètres par défaut avec **outils** > **Import and Export Paramètres** > **Réinitialiser tous les paramètres**. Pour réinitialiser un sous-ensemble de paramètres, enregistrez vos paramètres avec **l’Assistant Des Paramètres d’Importation et d’Exportation** avant d’effectuer les modifications que vous souhaitez tester, puis importez vos paramètres enregistrés par la suite.

Vous pouvez définir les options **générales** suivantes :

**Demandez avant de supprimer tous les points d’arrêt**: Nécessite une confirmation avant de compléter la commande **Supprimer tous les points de rupture.**

**Casser tous les processus lorsqu’un processus se brise**: Casse simultanément tous les processus auxquels le débbuggeur est attaché, lorsqu’une rupture se produit.

**Pause lorsque les exceptions traversent AppDomain ou les frontières gérées/autochtones**: Dans le débogage géré ou mixte, le temps d’exécution de la langue commune peut attraper des exceptions qui traversent les limites du domaine d’application ou les limites gérées/autochtones lorsque les conditions suivantes sont vraies :

1. Lorsque le code natif appelle le code managé à l'aide de COM Interop et que le code managé lève une exception. Voir [Introduction à COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quand le code managé s’exécutant dans le domaine d’application 1 appelle du code managé dans le domaine d’application 2 et que le code dans le domaine d’application 2 lève une exception. Consultez [Programmation avec des domaines d’application](/dotnet/articles/framework/app-domains/index).

3. Lorsque le code appelle une fonction en utilisant la réflexion, et cette fonction jette une exception. Voir [Réflexion](/dotnet/framework/reflection-and-codedom/reflection).

Dans les conditions 2 et 3, l’exception est parfois rattrapée par le code géré dans `mscorlib` plutôt que par l’heure courante. Cette option n'a aucune incidence sur l'arrêt sur les exceptions interceptées par `mscorlib`.

**Activer le débogage au niveau de l’adresse**: Permet des fonctionnalités avancées pour le débogage au niveau de l’adresse (la fenêtre **démontage,** la fenêtre **des registres** et les points d’arrêt d’adresse).

- **Afficher le démontage si la source n’est pas disponible**: affiche automatiquement la fenêtre **de démontage** lorsque vous débaillez le code pour lequel la source n’est pas disponible.

**Activez les filtres à points de rupture**: vous permet de définir des filtres sur des points de rupture afin qu’ils n’affectent que des processus, des threads ou des ordinateurs spécifiques.

**Utilisez le nouvel assistant d’exception**: Permet l’aide d’exception qui remplace l’assistant d’exception. (Exception Helper est pris en charge à partir de Visual Studio 2017)

> [!NOTE]
> Pour le code géré, cette option s’appelait auparavant **Enable l’assistant d’exception** .

**Activez Just My Code**: Le débogage s’affiche et entre dans le code utilisateur (« Mon Code ») seulement, ignorant le code système et d’autres codes optimisés ou qui n’ont pas de symboles de débogage.

- **Avertissez si aucun code utilisateur sur le lancement (géré uniquement)**: Lorsque le débogage commence avec Just My Code activé, cette option vous avertit s’il n’y a pas de code utilisateur (« Mon code »).

**Activez .NET Framework source stepping**: Permet au débbuggeur d’entrer dans la source cadre .NET. L’activation de cette option désactive automatiquement Just My Code. .NET Les symboles du Cadre seront téléchargés sur un emplacement de cache. Modifier l’emplacement du cache avec la boîte de dialogue **Options,** **catégorie Debugging,** **Page Symboles.**

**Étape sur les propriétés et les opérateurs (Géré uniquement)**: Empêche le débbuggeur d’entrer dans les propriétés et les opérateurs dans le code géré.

**Activer l’évaluation des biens et d’autres appels de fonction implicite**: Active l’évaluation automatique des propriétés et des appels de fonction implicite dans les fenêtres variables et la boîte de dialogue **QuickWatch.**

- **Fonction de conversion de chaîne d’appels sur des objets dans les fenêtres variables (C et JavaScript uniquement)**: Exécute un appel implicite de conversion de chaîne lors de l’évaluation des objets dans les fenêtres variables. Le résultat est affiché comme une chaîne au lieu du nom de type. S'applique uniquement lors du débogage en code C#. Ce paramètre peut être remplacé par l’attribut DebuggerDisplay (voir [Utiliser l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Activez**le support serveur source : Indique au visual Studio débogénaire d’obtenir`srcsrv.dll`des fichiers source à partir de serveurs sources qui implémentent le protocole SrcSrv () . Team Foundation Server et les outils de débogage pour Windows sont deux serveurs sources qui implémentent le protocole. Pour plus d’informations sur la configuration SrcSrv, voir la documentation [SrcSrv.](/windows-hardware/drivers/debugger/srcsrv) En outre, voir [spécifier symbole (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> La lecture des fichiers* .pdb* pouvant exécuter du code arbitraire dans les fichiers, vérifiez que le serveur possède un niveau de confiance suffisant.

- **Imprimez des messages diagnostiques de serveur source à la fenêtre de sortie**: Lorsque le support du serveur source est activé, ce paramètre s’active sur l’affichage diagnostique.

- **Autoriser le serveur source pour les assemblages de confiance partiels (géré uniquement)**: Lorsque le support du serveur source est activé, ce paramètre remplace le comportement par défaut de ne pas récupérer les sources pour les assemblages de confiance partiels.

- **Toujours exécuter des commandes de serveur source non fiable sans incitation**: Lorsque le support du serveur source est activé, ce paramètre remplace le comportement par défaut d’incitation lors de l’exécution d’une commande non fiable.

**Activer le support Source Link**: Indique au visual Studio debugger de télécharger des fichiers sources pour les fichiers *.pdb* qui contiennent des informations Source Link. Pour plus d’informations sur Source Link, voir la [spécification de lien Source](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Parce que Source Link téléchargera des fichiers à l’aide de https ou https, assurez-vous de faire confiance au fichier *.pdb.*

- **Revenez à l’authentification Git Credential Manager pour toutes les demandes source Link**: Lorsque le support Source Link est activé, et qu’une demande source Link échoue à l’authentification, Visual Studio appelle alors le gestionnaire d’informations d’identification Git.

**Mettre en évidence la ligne entière pour les points d’arrêt et l’énoncé actuel (C seulement)**: Lorsque le débbuggeur met en évidence un point d’arrêt ou une déclaration actuelle, il met en évidence l’ensemble de la ligne.

**Exigez que les fichiers sources correspondent exactement à la version originale**: indique au débogage de vérifier qu’un fichier source correspond à la version du code source utilisée pour construire l’exécutable que vous débogiez. Lorsque la version ne correspond pas, vous êtes invité à trouver une source correspondante. Si aucune source correspondante n'est trouvée, le code source n'est pas affiché pendant le débogage.

**Rediriger tout le texte de la fenêtre de sortie vers la fenêtre immédiate**: Envoie tous les messages de débbuggeur qui apparaîtraient habituellement dans la fenêtre de **sortie** vers la fenêtre **immédiate** à la place.

**Afficher la structure brute des objets dans les fenêtres variables**: éteint toutes les personnalisations de vue de la structure d’objets. Pour plus d’informations sur les personnalisations de vue, voir [Créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-managed-objects.md).

**Supprimer l’optimisation JIT sur la charge du module (Géré uniquement)**: désactive l’optimisation JIT du code géré lorsqu’un module est chargé et JIT est compilé pendant que le débbuggeur est attaché. La désactivation de l'optimisation peut simplifier le débogage de certains problèmes, mais elle se fait au détriment des performances. Si vous utilisez Uniquement mon code, la suppression de l'optimisation JIT peut entraîner l'affichage du code non-utilisateur comme du code utilisateur (« Mon code »). Pour plus d’informations, voir [L’optimisation et le débogage de JIT](../debugger/jit-optimization-and-debugging.md).

**Activez le débogage JavaScript pour ASP.NET (Chrome, Microsoft Edge et IE)**: Permet le débogage de script pour ASP.NET applications. Lors de la première utilisation dans Chrome, vous devrez peut-être vous connecter au navigateur pour activer les extensions Chrome que vous avez installées. Désactiver cette option pour revenir au comportement hérité.

**Activez les outils de développeur Edge pour UWP JavaScript Apps (Experimental)**: Permet des outils de développement pour les applications JavaScript UWP dans Microsoft Edge.

**Activez l’héritage Chrome JavaScript debugger pour ASP.NET**: Permet l’héritage Chrome JavaScript script debugger pour ASP.NET applications. Lors de la première utilisation dans Chrome, vous devrez peut-être vous connecter au navigateur pour activer les extensions Chrome que vous avez installées.

**Utilisez une façon expérimentale pour lancer Chrome JavaScript de débogage lors de l’exécution Visual Studio en tant qu’administrateur**: Tells Visual Studio pour essayer une nouvelle façon de lancer Chrome pendant le débogage JavaScript.

**Exportations de dll de charge (native seulement)**: Charges dll tables d’exportation. Les informations symboliques de tables d’exportation de dll peuvent être utiles si vous utilisez des messages Windows, des procédures Windows (WindowProcs), des objets COM, le marshaling ou toute dll pour laquelle vous n’avez pas de symbole. La lecture des informations d’exportation des dll implique une certaine charge mémoire. Par conséquent, cette fonctionnalité est désactivée par défaut.

Pour savoir quels symboles sont disponibles dans la table d’exportation d’une dll, utilisez `dumpbin /exports`. Il existe des symboles pour toutes les dll système 32 bits. En lisant le résultat de `dumpbin /exports` , vous apprenez le nom exact de la fonction, y compris les caractères non alphanumériques. Cette information peut être utile pour définir un point d'arrêt sur une fonction. Les noms de fonctions provenant de tables d’exportation de dll peuvent s’afficher sous une forme tronquée dans les autres parties du débogueur. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours (la plus profondément imbriquée) apparaissant en tête de liste. Pour plus d'informations, consultez [dumpbin /exports](/cpp/build/reference/dash-exports).

**Afficher les piles parallèles diagramme bas en haut**: Contrôle la direction dans laquelle les piles sont affichées dans la fenêtre Parallel **Stacks.**

**Ignorer les exceptions d’accès à la mémoire GPU si les données écrites n’ont pas changé la valeur**: Ignore les conditions de course qui ont été détectées lors de l’insuffisance si les données n’ont pas changé. Pour plus d’informations, voir [Debugging GPU Code](../debugger/debugging-gpu-code.md).

**Utiliser le mode de compatibilité gérée**: remplace le moteur de débogage par défaut par une version héritée pour activer ces scénarios :

- Vous utilisez un langage .NET autre que C, Visual Basic ou Fmd qui fournit son propre évaluateur d’expression (cela inclut CMD/CLI).

- Vous souhaitez activer Edit and Continue pour les projets CMD lors du débogage en mode mixte.

> [!NOTE]
> Le choix du mode de compatibilité gérée désactive certaines fonctionnalités qui ne sont mises en œuvre que dans le moteur de débogage par défaut. L’héritage moteur de débogage a été remplacé dans Visual Studio 2012.

**Utilisez les évaluateurs d’expression C et VB existants**: Le débbuggeur utilisera les évaluateurs d’expression Visual Studio 2013 C OU Visual Basic plutôt que les évaluateurs d’expression basés sur Le Studio Visuel 2015 basé à Roslyn.

**Avertissez-vous lorsque vous utilisez des visualisateurs de débbugger personnalisés contre les processus potentiellement dangereux (géré seulement)**: Visual Studio vous avertit lorsque vous utilisez un visualiseur de débbugger personnalisé qui exécute du code dans le processus débogé, car il pourrait être en cours d’exécution de code dangereux.

**Activez l’alloueur de tas de débouge de Windows (native seulement)**: Permet au tas de débouge de fenêtres d’améliorer les diagnostics de tas. L’activation de cette option affecte les performances de débogage.

**Activez UI Debugging Tools pour XAML**: L’arbre visuel en direct et les fenêtres Live Property Explore apparaîtront lorsque vous commencerez à débogage (**F5**) un type de projet pris en charge. Pour plus d’informations, voir [Inspecter les propriétés XAML tout en débogage](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Aperçu d’éléments sélectionnés dans Live Visual Tree**: L’élément XAML dont le contexte est sélectionné est également sélectionné dans la fenêtre Live Visual **Tree.**

- **Afficher les outils d’exécution en application**: Affiche les commandes **Live Visual Tree** dans une barre d’outils sur la fenêtre principale de l’application XAML qui est en cours de déboguer. Cette option a été introduite dans Visual Studio 2015 Update 2.

- **Activez XAML Hot Reload**: vous permet d’utiliser la fonction XAML Hot Reload avec le code XAML lorsque votre application est en cours d’exécution. (Cette fonctionnalité a été précédemment appelée "XAML Edit and Continue")

::: moniker range=">= vs-2019" 
- **Activer Just My XAML**: À partir de Visual Studio 2019 version 16.4, **l’arbre visuel en direct** affiche par défaut uniquement XAML qui est classé comme code utilisateur. Si vous désactivez cette option, tout le code XAML généré est affiché dans l’outil.

- **Désactiver le mode de sélection lorsqu’un élément est sélectionné** À partir de Visual Studio 2019 version 16.4, le bouton de sélecteur d’éléments de barre d’outils in-app (**Activer la sélection**) s’éteint lorsqu’un élément est sélectionné. Si vous désactivez cette option, la sélection des éléments reste allumée jusqu’à ce que vous cliquez à nouveau sur le bouton de la barre d’outils in-app.
::: moniker-end

**Activez les outils diagnostiques tout en débogage**: La fenêtre **Des outils diagnostiques** apparaît pendant que vous débogiez.

**Afficher le temps écoulé PerfTip tout en débogage**: La fenêtre de code affiche le temps écoulé d’un appel de méthode donné lorsque vous débogage.

**Activez Edit and Continue**: Permet la fonctionnalité Edit and Continue tout en débogage.

- **Activez Native Edit and Continue**: Vous pouvez utiliser la fonctionnalité Edit and Continue tout en débogage du code CMD natif. Pour plus d’informations, voir [Edit and Continue (C)](../debugger/edit-and-continue-visual-cpp.md).

- **Appliquez les modifications sur la poursuite (native seulement)**: Visual Studio compile automatiquement et applique toutes les modifications de code en suspens que vous avez apportées lors de la poursuite du processus à partir d’un état de rupture. S’il n’est pas sélectionné, vous pouvez choisir d’appliquer des modifications à l’aide de **l’élément modification du code d’application** dans le cadre du menu **Debug.**

- **Avertissement sur le code périmé (native seulement)**: Obtenez des avertissements sur le code périmé.

**Afficher le bouton Run to Click dans l’éditeur tout en débogage**: Lorsque cette option est sélectionnée, le bouton [Run to Click](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) sera affiché lors du débogage.

**Fermez automatiquement la console lorsque le débogage s’arrête**: indique à Visual Studio de fermer la console à la fin d’une séance de débogage.

::: moniker range=">= vs-2019"
**Activez l’évaluation de l’expression rapide (gérée uniquement)**: Permet au débbuggeur de tenter une évaluation plus rapide en simulant l’exécution de propriétés et de méthodes simples.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Options disponibles dans les anciennes versions de Visual Studio

Si vous utilisez une ancienne version de Visual Studio, certaines options supplémentaires pourraient être présentes.

**Activez l’assistant d’exception**: Pour le code géré, permet l’assistant d’exception. À partir de Visual Studio 2017, l’Exception Helper a remplacé l’assistant d’exception.

**Dénouer la pile d’appels sur des exceptions non gérées**: provoque la fenêtre **De la pile d’appels** pour faire reculer la pile d’appels au point avant que l’exception non gérée ne se produise.

**Avertissez si aucun symbole sur le lancement (natif seulement)**: Affiche une boîte de dialogue d’avertissement lorsque vous débbug un programme pour lequel le débbuggeur n’a aucune information de symbole.

**Avertissez si le débogage de script est désactivé au lancement**: affiche une boîte de dialogue d’avertissement lorsque le débbuggeur est lancé avec le script débogage désactivé.

**Utilisez le mode de compatibilité native**: Lorsque cette option est sélectionnée, le débbuggeur utilise le débbuggeur natif Visual Studio 2010 au lieu du nouveau débbugger indigène.

- Utilisez cette option lorsque vous débogage .NET C 'code, parce que le nouveau moteur de débogage ne prend pas en charge l’évaluation des expressions .NET C ' Toutefois, l’activation du mode de compatibilité natif désactive de nombreuses fonctionnalités qui dépendent de l’implémentation du débogueur actuel pour fonctionner. Par exemple, l’ancien moteur manque de nombreux visualisateurs pour les types intégrés comme `std::string` dans les projets Visual Studio 2015.   Utilisez les projets Visual Studio 2013 pour l’expérience optimale de débogage dans ces cas.

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Premier regard sur le débbugger](../debugger/debugger-feature-tour.md)
