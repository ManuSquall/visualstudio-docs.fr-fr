---
title: Général, débogage, de boîte de dialogue Options | Microsoft Docs
ms.date: 11/09/2018
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
ms.openlocfilehash: 2e97f2f844c53a6bf26fecc4559b65ae69970c6b
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526537"
---
# <a name="general-debugging-options"></a>Options de débogage générales

Pour définir les options du débogueur Visual Studio, sélectionnez **outils** > **Options**, puis, sous **débogage** Sélectionnez ou désélectionnez les cases à côté du  **Général** options. Vous pouvez restaurer tous les paramètres par défaut avec **outils** > **importation et exportation de paramètres** > **réinitialiser tous les paramètres**. Pour réinitialiser un sous-ensemble de paramètres, enregistrez vos paramètres avec le **Assistant Importation et exportation paramètres** avant d’apporter les modifications que vous souhaitez tester, puis importer vos paramètres enregistrés par la suite.

Vous pouvez définir les éléments suivants **général** options :

**Demander avant de supprimer tous les points d’arrêt**: exige une confirmation avant la fin de la **supprimer tous les points d’arrêt** commande.

**Arrêter tous les processus lorsqu’un processus s’arrête**: arrête simultanément tous les processus auxquels le débogueur est attaché, lorsqu’un arrêt se produit.

**Arrêter lorsque des exceptions dépassent les limites AppDomain ou managées/natives**: lors du débogage managé ou en mode mixte, le common language runtime peut intercepter les exceptions qui traversent les limites du domaine d’application ou les limites managées/natives lorsque les éléments suivants conditions sont remplies :

1. Lorsque le code natif appelle le code managé à l'aide de COM Interop et que le code managé lève une exception. Consultez [Introduction à COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quand le code managé s’exécutant dans le domaine d’application 1 appelle du code managé dans le domaine d’application 2 et que le code dans le domaine d’application 2 lève une exception. Consultez [Programmation avec des domaines d’application](/dotnet/articles/framework/app-domains/index).

3. Lorsque le code appelle une fonction en utilisant la réflexion, et que fonction lève une exception. Consultez [réflexion](/dotnet/framework/reflection-and-codedom/reflection).

Dans les conditions 2 et 3, l’exception est quelquefois interceptée par le code managé dans `mscorlib` plutôt que par le common language runtime. Cette option n'a aucune incidence sur l'arrêt sur les exceptions interceptées par `mscorlib`.

**Activer le débogage au niveau des adresses**: Active les fonctionnalités avancées pour le débogage au niveau de l’adresse (la **désassemblage** fenêtre, le **inscrit** fenêtre et les points d’arrêt de l’adresse).

- **Afficher le code machine si la source n’est pas disponible**: affiche automatiquement le **désassemblage** fenêtre lorsque vous déboguez du code pour lequel la source n’est pas disponible.

**Activer les filtres de point d’arrêt**: vous permet de définir des filtres sur des points d’arrêt afin qu’ils affectent uniquement des processus, threads ou ordinateurs.

**La nouvelle assistance d’Exception**: permet à l’assistance de l’Exception qui remplace l’assistant exception. (Assistance d’exception est pris en charge dans Visual Studio 2017)

> [!NOTE]
> Pour le code managé, cette option s’appelait précédemment **activer l’assistant exception** .

**Activer uniquement mon Code**: le débogueur affiche et les étapes dans le code utilisateur (« mon Code ») uniquement, en ignorant le code système et tout autre code optimisé ou qui n’a pas de symboles de débogage.

- **Avertir si aucun code utilisateur au lancement (managé uniquement)**: démarrage du débogage avec uniquement mon Code est activée, cette option vous avertit s’il n’existe aucun code utilisateur (« mon Code »).

**Activer .NET Framework pas à pas détaillé de la source**: permet au débogueur d’étape dans la source du .NET Framework. L’activation cette option désactive automatiquement uniquement mon Code. .NET framework symboles seront téléchargés vers un emplacement de cache. Modifier l’emplacement du cache avec le **Options** boîte de dialogue, **débogage** catégorie, **symboles** page.

**Pas à pas principal des propriétés et les opérateurs (managé uniquement)**: empêche le débogueur d’exécution pas à pas détaillé des propriétés et des opérateurs en code managé.

**Activer l’évaluation de la propriété et d’autres appels de fonction implicite**: Active l’évaluation automatique de propriétés et de fonction implicite appels dans des fenêtres de variables et les **Espion express** boîte de dialogue.

- **Appeler la fonction de conversion de chaînes sur des objets dans des fenêtres de variables (C# et JavaScript uniquement)**: exécute un appel de conversion de chaînes implicite lors de l’évaluation des objets dans des fenêtres de variables. Le résultat est affiché sous forme de chaîne au lieu du nom de type. S'applique uniquement lors du débogage en code C#. Ce paramètre peut être substitué par l’attribut DebuggerDisplay (consultez [à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Activer la prise en charge du serveur source**: indique au débogueur de Visual Studio pour obtenir des fichiers sources à partir de serveurs sources qui implémentent le SrcSrv (`srcsrv.dll`) protocole. Team Foundation Server et les outils de débogage pour Windows sont deux serveurs sources qui implémentent le protocole. Pour plus d’informations sur le programme d’installation de SrcSrv, consultez la [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) documentation. En outre, consultez [spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> La lecture des fichiers *.pdb* pouvant exécuter du code arbitraire dans les fichiers, vérifiez que le serveur possède un niveau de confiance suffisant.

- **Afficher les messages de diagnostic du serveur source dans la fenêtre sortie**: lors de la prise en charge du serveur source est activé, ce paramètre Active l’affichage de diagnostic.

- **Autoriser le serveur source pour les assemblys de confiance partielle (managé uniquement)**: lors de la prise en charge du serveur source est activé, ce paramètre remplace le comportement par défaut de non récupération des sources pour les assemblys de confiance partielle.

- **Toujours exécuter les commandes du serveur source non fiables sans demander confirmation**: lors de la prise en charge du serveur source est activé, ce paramètre remplace le comportement par défaut d’invites lors de l’exécution d’une commande non approuvée.

**Activer la prise en charge de Sourcelink**: indique au débogueur de Visual Studio pour télécharger les fichiers source pour *.pdb* fichiers qui contiennent des informations de lien Source. Pour plus d’informations sur le lien Source, consultez la [spécification du lien Source](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
>  Étant donné que le lien Source sera téléchargé les fichiers à l’aide de http ou https, assurez-vous que vous faites confiance à la *.pdb* fichier.

- **Passage à l’authentification Git Credential Manager pour toutes les demandes de liaison de Source**: prise en charge lors de la liaison de Source est activée, et une demande de lien Source fait échouer l’authentification, Visual Studio, puis appelle le Gestionnaire d’informations d’identification Git.

**Mettez en surbrillance la ligne entière pour les points d’arrêt et l’instruction actuelle (C++ uniquement)**: lorsque le débogueur met en surbrillance un point d’arrêt et l’instruction actuelle, il met en surbrillance la ligne entière.

**Les fichiers sources doivent correspondre exactement à la version d’origine**: indique au débogueur pour vérifier qu’un fichier source correspond à la version du code source utilisé pour générer le fichier exécutable que vous déboguez. Lorsque la version ne correspond pas, vous êtes invité à rechercher une source correspondante. Si aucune source correspondante n'est trouvée, le code source n'est pas affiché pendant le débogage.

**Rediriger tout le texte fenêtre Sortie vers la fenêtre exécution**: envoie tous les messages du débogueur qui seraient affichent normalement dans les **sortie** fenêtre pour le **immédiat** fenêtre à la place.

**Afficher la structure brute des objets dans des fenêtres de variables**: désactive toutes les personnalisations d’affichage de structure objet. Pour plus d’informations sur les personnalisations d’affichage, consultez [créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-dot-managed-objects.md).

**Supprimer l’optimisation JIT lors du chargement de module (managé uniquement)**: désactive l’optimisation JIT du code managé lorsqu’un module est chargé et que JIT est compilé pendant que le débogueur est attaché. La désactivation de l'optimisation peut simplifier le débogage de certains problèmes, mais elle se fait au détriment des performances. Si vous utilisez Uniquement mon code, la suppression de l'optimisation JIT peut entraîner l'affichage du code non-utilisateur comme du code utilisateur (« Mon code »). Pour plus d’informations, consultez [JIT optimisation et débogage](../debugger/jit-optimization-and-debugging.md).

**Activer le débogage de JavaScript pour ASP.NET (Chrome, Edge et IE)**: permet au débogueur de script pour les applications ASP.NET. À la première utilisation dans Chrome, vous devrez peut-être vous connecter dans le navigateur pour activer les extensions de Chrome que vous avez installée. Désactivez cette option pour rétablir le comportement hérité.

**Activer les outils de développement Edge pour les applications JavaScript UWP (expérimental)**: Active les outils de développement pour applications UWP JavaScript dans Edge.

**Activer le débogueur de Chrome JavaScript hérité pour ASP.NET**: permet au débogueur de script JavaScript de Chrome hérité pour les applications ASP.NET. À la première utilisation dans Chrome, vous devrez peut-être vous connecter dans le navigateur pour activer les extensions de Chrome que vous avez installée.

**Utiliser de façon expérimentale pour lancer le débogage de JavaScript de Chrome lors de l’exécution de Visual Studio en tant qu’administrateur**: indique à Visual Studio pour essayer une nouvelle façon de lancer Chrome pendant le débogage de JavaScript.

**Charger les exportations de dll (natif uniquement)**: charge les tables d’exportation de dll. Les informations symboliques de tables d’exportation de dll peuvent être utiles si vous utilisez des messages Windows, des procédures Windows (WindowProcs), des objets COM, le marshaling ou toute dll pour laquelle vous n’avez pas de symbole. La lecture des informations d’exportation des dll implique une certaine charge mémoire. Par conséquent, cette fonctionnalité est désactivée par défaut.

Pour savoir quels symboles sont disponibles dans la table d’exportation d’une dll, utilisez `dumpbin /exports`. Il existe des symboles pour toutes les dll système 32 bits. En lisant le résultat de `dumpbin /exports` , vous apprenez le nom exact de la fonction, y compris les caractères non alphanumériques. Cette information peut être utile pour définir un point d'arrêt sur une fonction. Les noms de fonctions provenant de tables d’exportation de dll peuvent s’afficher sous une forme tronquée dans les autres parties du débogueur. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours (la plus profondément imbriquée) apparaissant en tête de liste. Pour plus d'informations, consultez [dumpbin /exports](/cpp/build/reference/dash-exports).

**Afficher des piles parallèles diagramme ascendant**: contrôle la direction dans laquelle les piles sont affichées dans le **piles parallèles** fenêtre.

**Ignorer les exceptions d’accès mémoire GPU si les données écrites n’a pas modifié la valeur**: ignore les conditions de concurrence qui ont été détectées pendant le débogage si les données n’ont pas modifié. Pour plus d’informations, consultez [débogage du Code GPU](../debugger/debugging-gpu-code.md).

**Utiliser le Mode de compatibilité managé**: remplace la valeur par défaut de moteur avec une version héritée pour activer les scénarios de débogage :

- Vous utilisez un langage .NET Framework autre que C#, Visual Basic, ou F# qui fournit son propre évaluateur d’Expression (y compris C++ / c++ / CLI).

- Vous souhaitez activer Modifier & Continuer pour les projets C++ pendant le débogage en mode mixte.

> [!NOTE]
> Choix de compatibilité managé désactive certaines fonctionnalités qui sont implémentées uniquement dans le moteur de débogage par défaut. Le moteur de débogage hérité a été remplacé dans Visual Studio 2012.

**Utiliser l’ancien C# et évaluateurs d’expression VB**: le débogueur utilisera le Visual Studio 2013 C# ou évaluateurs d’expression Visual Basic plutôt que les évaluateurs d’expression Visual Studio 2015 de roslyn.

**Avertir en cas d’utilisation de visualiseurs de débogueur personnalisés avec des processus potentiellement unsafe (managé uniquement)**: Visual Studio vous avertit lorsque vous utilisez un visualiseur du débogueur personnalisé qui exécute le code dans le processus débogué, car il peut être en cours d’exécution code unsafe.

**Activer l’allocateur de tas de débogage Windows (natif uniquement)**: permet le tas de débogage windows améliorer les diagnostics de segment de mémoire. L’activation de cette option affecte les performances de débogage.

**Activer les outils de débogage de l’interface utilisateur pour XAML**: le Live Visual Tree et les fenêtres d’Explorateur de propriétés en direct seront affiche lorsque vous démarrez le débogage (**F5**) un type de projet pris en charge. Pour plus d’informations, consultez [propriétés XAML inspecter pendant le débogage](../debugger/inspect-xaml-properties-while-debugging.md).

- **Afficher un aperçu des éléments sélectionnés dans l’arborescence d’éléments visuels en direct**: élément le XAML dont le contexte est sélectionné est également sélectionné dans le **Live Visual Tree** fenêtre.

- **Afficher les outils de runtime dans application**: montre la **Live Visual Tree** commandes dans une barre d’outils de la fenêtre principale de l’application XAML en cours de débogage. Cette option a été introduite dans Visual Studio 2015 Update 2.

- **Activer XAML modifier et continuer**: vous permet d’utiliser le modifier et continuer la fonction avec le code XAML.

**Activer les outils de Diagnostic pendant le débogage**: le **outils de Diagnostic** fenêtre s’affiche lorsque vous déboguez.

**Afficher le PerfTip du temps écoulé durant le débogage**: la fenêtre de code affiche le temps écoulé d’un appel de méthode donné lors du débogage.

**Activer Modifier & Continuer**: Active la fonctionnalité Modifier & Continuer pendant le débogage.

- **Activer Modifier et continuer natif**: vous pouvez utiliser le modifier et continuer de fonctionnalité lors du débogage du code C++ natif. Pour plus d’informations, consultez [Modifier & Continuer (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Appliquer les changements en continuant (natif uniquement)**: Visual Studio compile automatiquement et applique les modifications de code en attente apportées lors de la poursuite du processus à partir d’un état d’arrêt. Si cette option n’est pas sélectionnée, vous pouvez choisir d’appliquer les modifications à l’aide de l’élément **Appliquer les modifications du code** dans le menu **Déboguer**.

- **Signaler le code périmé (natif uniquement)**: obtenez des avertissements concernant le code périmé.

**Afficher l’exécution à, cliquez sur bouton dans l’éditeur lors du débogage**: lorsque cette option est sélectionnée, le [exécuter jusqu’au clic](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) bouton s’affichera lors du débogage.

**Fermer automatiquement la console lorsque le débogage s’arrête**: indique à Visual Studio pour fermer la console à la fin d’une session de débogage.

## <a name="options-available-in-older-versions-of-visual-studio"></a>Options disponibles dans les versions antérieures de Visual Studio

Si vous utilisez une version antérieure de Visual Studio, des options supplémentaires peuvent être présentes.

**Activer l’assistant exception**: pour le code managé, permet à l’assistant exception. À partir de Visual Studio 2017, l’assistance d’Exception remplacé l’assistant exception.

**Dérouler la pile des appels sur les exceptions non gérées**: provoque la **pile des appels** fenêtre restaure la pile des appels au point qui précède l’exception non gérée s’est produite.

**Avertir si aucun symbole au lancement (natif uniquement)**: affiche une boîte de dialogue d’avertissement lorsque vous déboguez un programme pour lequel le débogueur ne possède aucune information de symbole.

**Avertir si le débogage de script est désactivé au lancement**: affiche une boîte de dialogue d’avertissement lorsque le débogueur est lancé avec le débogage de script est désactivé.

**Utilisez le Mode de compatibilité natif**: lorsque cette option est sélectionnée, le débogueur utilise le débogueur natif Visual Studio 2010 au lieu du nouveau débogueur natif.

- Utilisez cette option lorsque vous déboguez le code .NET C++, car le nouveau moteur de débogage ne prend pas en charge l’évaluation des expressions .NET C++. Toutefois, l’activation du mode de compatibilité natif désactive de nombreuses fonctionnalités qui dépendent de l’implémentation du débogueur actuel pour fonctionner. Par exemple, le moteur hérité ne dispose pas de nombreux visualiseurs pour les types intégrés tels que `std::string` dans les projets Visual Studio 2015.   Utiliser des projets Visual Studio 2013 pour l’expérience de débogage optimale dans ces cas.

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)