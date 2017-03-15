---
title: "G&#233;n&#233;ral, D&#233;bogage, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.General"
  - "VS.ToolsOptionsPages.Debugger.General"
  - "VS.ToolsOptionsPages.Debugger.ENC"
  - "vs.debug.options.ENC"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Options (boîte de dialogue), débogage"
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 46
caps.handback.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# G&#233;n&#233;ral, D&#233;bogage, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La page **Outils\/Options\/Débogage\/Général** vous permet de définir les options suivantes :  
  
 **Demander avant de supprimer tous les points d'arrêt**  
 Exige une confirmation avant l'exécution de la commande **Supprimer tous les points d'arrêt**.  
  
 **Arrêter tous les processus lorsqu'un processus s'arrête**  
 Arrête simultanément tous les processus auxquels le débogueur est associé, lorsqu'un arrêt se produit.  
  
 **Arrêter lorsque des exceptions dépassent les limites AppDomain ou managées\/natives**  
 Lors du débogage managé ou en mode mixte, le Common Language Runtime peut intercepter les exceptions qui transgressent les limites entre domaines d'application ou les limites managées\/natives dans les conditions suivantes :  
  
 1\) Lorsque le code natif appelle le code managé à l'aide de COM Interop et que le code managé lève une exception. Consultez [Introduction to COM Interop](/dotnet/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
 2\) Quand le code managé s’exécutant dans le domaine d’application 1 appelle du code managé dans le domaine d’application 2 et que le code dans le domaine d’application 2 lève une exception. Consultez [Programmation avec des domaines d’application](http://msdn.microsoft.com/fr-fr/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) Lorsque le code appelle une fonction à l'aide de la réflexion et que la fonction lève une exception. Consultez [Réflexion](../Topic/Reflection%20in%20the%20.NET%20Framework.md).  
  
 Dans les conditions 2\) et 3\), l'exception est quelquefois interceptée par le code managé dans `mscorlib` au lieu du Common Language Runtime. Cette option n'a aucune incidence sur l'arrêt sur les exceptions interceptées par `mscorlib`.  
  
 **Activer le débogage au niveau de l'adresse**  
 Active les fonctionnalités avancées pour le débogage au niveau de l'adresse \(la fenêtre **Code machine**, la fenêtre **Registres** et les points d'arrêt sur adresse mémoire\).  
  
 **Afficher le code machine si la source n'est pas disponible**  
 Affiche automatiquement la fenêtre **Code Machine** lorsque vous essayez de déboguer du code pour lequel la source n'est pas disponible.  
  
 **Activer les filtres de point d'arrêt**  
 Vous permet de définir des filtres sur les points d'arrêt afin qu'ils affectent uniquement des processus, threads ou ordinateurs spécifiques.  
  
 **Activer l'Assistant Exception**  
 Pour code managé uniquement. Les exceptions prises en charge ouvrent la boîte de dialogue Assistant Exception.  Consultez [Exception Assistant](../Topic/Exception%20Assistant.md).  
  
 **Dérouler la pile des appels sur les exceptions non gérées**  
 La fenêtre **Pile des appels** restaure la pile des appels au point qui précède l'exception non gérée.  
  
 **Activer Uniquement mon code**  
 Le débogueur affiche et exécute pas à pas le code utilisateur \(« Mon code »\) uniquement et il ignore le code système et tout autre code optimisé ou ne possédant pas de symboles de débogage.  
  
 **Afficher tous les membres pour les objets non\-utilisateur dans des fenêtres de variables \(Visual Basic uniquement\)**  
 Active l'affichage des membres non publics dans les objets qui sont en code non\-utilisateur \(pas « Mon code »\).  
  
 **Avertir s'il n'y a pas de code utilisateur au lancement**  
 Lorsque le débogage commence et que l'option Uniquement mon code est activée, cette option vous avertit en cas d'absence de code utilisateur \(« Mon code »\).  
  
 **Activer l'exécution pas à pas du code source du .NET Framework**  
 Permet au débogueur d'effectuer un pas à pas détaillé dans la source .NET Framework. L'activation de cette option désactive automatiquement Uniquement mon code. Les symboles .NET Framework sont téléchargés dans un emplacement du cache. Vous pouvez modifier cet emplacement dans la boîte de dialogue **Options**, catégorie **Débogage**, page **Symboles**.  
  
 **Pas à pas principal dans les propriétés et les opérateurs \(managé uniquement\)**  
 Empêche le débogueur d'effectuer un pas à pas détaillé des propriétés et des opérateurs en code managé.  
  
 **Activer l'évaluation de la propriété et d'autres appels de fonction implicite**  
 Active l'évaluation automatique des propriétés et des appels de fonction implicites dans les fenêtres de variables et la boîte de dialogue **Espion express**.  
  
 **Appeler la fonction de conversion de chaînes pour les objets dans des fenêtres de variables \(C\# et JavaScript uniquement\)**  
 Exécute un appel de conversion de chaînes implicite lors de l'évaluation d'objets dans des fenêtres de variables. Par conséquent, ce résultat est affiché sous forme de chaîne plutôt que sous forme de nom de type. S'applique uniquement lors du débogage en code C\#. Ce paramètre peut être substitué par l’attribut DebuggerDisplay \(consultez [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)\).  
  
 **Activer le support du serveur source**  
 Indique au débogueur Visual Studio qu'il faut obtenir les fichiers sources à partir des serveurs sources qui implémentent le protocole SrcSrv \(`srcsrv.dll`\). Team Foundation Server et les outils de débogage pour Windows sont deux serveurs sources qui implémentent le protocole. Pour plus d'informations sur l'installation de SrcSrv, consultez la documentation des outils de débogage pour Windows. Consultez également [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  La lecture des fichiers .pdb pouvant exécuter du code arbitraire dans les fichiers, vérifiez que le serveur possède un niveau de confiance suffisant.  
  
 **Afficher les messages de diagnostic du serveur source dans la fenêtre Sortie**  
 Lorsque la prise en charge du serveur source est activée, ce paramètre active l'affichage des messages de diagnostic.  
  
 **Autoriser le serveur source pour les assemblys de confiance partielle \(Managé uniquement\)**  
 Lorsque la prise en charge du serveur source est activée, ce paramètre remplace le comportement par défaut qui consiste à ne pas récupérer les sources des assemblys de confiance partielle.  
  
 **Mettre en surbrillance l'intégralité de la ligne pour les points d'arrêt et l'instruction actuelle**  
 Lorsque le débogueur met en surbrillance un point d'arrêt ou l'instruction actuelle, il met en surbrillance la ligne entière.  
  
 **Les fichiers sources doivent correspondre exactement à la version d'origine**  
 Indique au débogueur de vérifier qu'un fichier source correspond à la version du code source utilisée pour générer le fichier exécutable que vous déboguez. Si la version ne correspond pas, vous êtes invité à rechercher une source correspondante. Si aucune source correspondante n'est trouvée, le code source n'est pas affiché pendant le débogage.  
  
 **Rediriger tout le texte de la fenêtre Sortie vers la fenêtre Exécution**  
 Envoie tous les messages du débogueur qui s'affichent normalement dans la fenêtre **Sortie** vers la fenêtre **Exécution**.  
  
 **Afficher la structure brute des objets dans des fenêtres de variables**  
 Désactive toutes les personnalisations d'affichage de la structure des objets. Pour plus d’informations sur les personnalisations d’affichage, consultez [Affichage des types de données personnalisés](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Supprimer l'optimisation JIT lors du chargement du module \(Managé uniquement\)**  
 Désactive l'optimisation JIT du code managé lorsqu'un module est chargé et que JIT est compilé pendant que le débogueur est attaché. La désactivation de l'optimisation peut simplifier le débogage de certains problèmes, mais elle se fait au détriment des performances. Si vous utilisez Uniquement mon code, la suppression de l'optimisation JIT peut entraîner l'affichage du code non\-utilisateur comme du code utilisateur \(« Mon code »\).  
  
 **Avertir s'il n'y a aucun symbole au lancement \(natif uniquement\)**  
 Cette option affiche une boîte de dialogue d’avertissement quand vous essayez de déboguer un programme pour lequel le débogueur ne possède aucune information symbolique.  
  
 **Avertir si le débogage des scripts est désactivé au lancement**  
 Cette option affiche une boîte de dialogue d’avertissement quand le débogueur est lancé alors que le débogage de script est désactivé.  
  
 **Charger les exportations de dll**  
 Cette option charge les tables d’exportation de dll. Les informations symboliques de tables d’exportation de dll peuvent être utiles si vous utilisez des messages Windows, des procédures Windows \(WindowProcs\), des objets COM, le marshaling ou toute dll pour laquelle vous n’avez pas de symbole. La lecture des informations d’exportation des dll implique une certaine charge mémoire. Par conséquent, cette fonctionnalité est désactivée par défaut.  
  
 Pour savoir quels symboles sont disponibles dans la table d’exportation d’une dll, utilisez `dumpbin /exports`. Il existe des symboles pour toutes les dll système 32 bits. En lisant le résultat de `dumpbin /exports`, vous apprenez le nom exact de la fonction, y compris les caractères non alphanumériques. Cette information peut être utile pour définir un point d'arrêt sur une fonction. Les noms de fonctions provenant de tables d’exportation de dll peuvent s’afficher sous une forme tronquée dans les autres parties du débogueur. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours \(la plus profondément imbriquée\) apparaissant en tête de liste. Pour plus d'informations, consultez [dumpbin \/exports](/visual-cpp/build/reference/dash-exports).  
  
 **Afficher le diagramme ascendant des piles parallèles**  
 Contrôle la direction dans laquelle les piles sont affichées dans la fenêtre **Piles parallèles**.  
  
 **Ignorer les exceptions d'accès à la mémoire GPU si les données écrites n'ont pas modifié la valeur**  
 Ignore les conditions de concurrence critique détectées pendant le débogage si les données n'ont pas changé. Pour plus d'informations, consultez [Débogage du code GPU](../debugger/debugging-gpu-code.md).  
  
 **Utiliser le mode de compatibilité managé**  
 Remplace le moteur de débogage par défaut par une version héritée pour activer les scénarios suivants :  
  
-   Vous utilisez un langage .NET Framework autre que C\#, VB ou F\# qui fournit son propre évaluateur d'expression \(y compris C\+\+\/CLI\).  
  
-   Vous souhaitez activer Modifier & Continuer pour les projets C\+\+ pendant le débogage en mode mixte.  
  
 Notez que le fait de choisir le mode de compatibilité managé désactive certaines fonctionnalités qui sont implémentées uniquement dans le moteur de débogage par défaut.  
  
 **Utiliser le mode de compatibilité natif**  
 Quand cette option est sélectionnée, le débogueur utilise le débogueur natif Visual Studio 2010 au lieu du nouveau débogueur natif.  
  
 Vous devez utiliser cette option quand vous déboguez le code .NET C\+\+, car le nouveau moteur de débogage ne prend pas en charge l’évaluation des expressions .NET C\+\+. Toutefois, l’activation du mode de compatibilité natif désactive de nombreuses fonctionnalités qui dépendent de l’implémentation du débogueur actuel pour fonctionner. Par exemple, le moteur hérité ne dispose pas de nombreux visualiseurs pour les types intégrés tels que `std::string` dans les projets Visual Studio 2015.   Utilisez les projets Visual Studio 2013 pour une expérience de débogage optimale dans ces cas.  
  
 **Utiliser les évaluateurs d'expressions C\# et VB hérités**  
 Le débogueur utilisera les évaluateurs d’expression Visual Studio 2013 C\#\/Visual Basic au lieu des évaluateurs d’expression Roslyn de Visual Studio 2015.  
  
 **Avertir en cas d’utilisation de visualiseurs de débogueur personnalisés avec du code potentiellement unsafe**  
 Visual Studio vous avertit quand vous utilisez un visualiseur de débogueur personnalisé qui exécute le code dans le processus du programme débogué, car il pourrait exécuter du code unsafe.  
  
 **Activer le débogage de l'allocateur de tas Windows \(Natif uniquement\)**  
 Permet au tas de débogage Windows d’améliorer les diagnostics du tas. L’activation de cette option affecte les performances de débogage.  
  
 **Activer les outils de débogage d'interface utilisateur pour XAML**  
 Les fenêtres Arborescence d’éléments visuels en direct et Explorateur de propriétés en direct s’affichent quand vous démarrez le débogage \(F5\) d’un type de projet pris en charge. Pour plus d'informations, consultez [Inspecter les propriétés XAML en phase de débogage](../debugger/inspect-xaml-properties-while-debugging.md).  
  
 **Afficher l'aperçu des éléments sélectionnés dans l'arborescence d'éléments visuels en direct**  
 L’élément XAML dont le contexte est sélectionné est également sélectionné dans la fenêtre Arborescence d’éléments visuels en direct.  
  
 **Activer les outils de diagnostic durant le débogage**  
 La fenêtre Outils de diagnostic s’affiche pendant que vous déboguez. Pour plus d'informations, consultez [Diagnostics intégrés au débogueur](../Topic/Debugger-integrated%20profiling.md).  
  
 **Afficher le PerfTip du temps écoulé durant le débogage**  
 La fenêtre de code affiche le temps écoulé d’un appel de méthode donné lors du débogage.  
  
 **Activer Modifier et Continuer**  
 Vous pouvez utiliser la fonctionnalité Modifier & Continuer pendant le débogage.  
  
 **Activer Modifier et Continuer natif**  
 Vous pouvez utiliser la fonctionnalité Modifier & Continuer pendant le débogage du code C\+\+ natif. Pour plus d'informations, consultez [Modifier & Continuer \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 **Appliquer les changements en continuant \(natif uniquement\)**  
 Visual Studio compile et applique automatiquement les modifications de code en attente apportées lors de la poursuite du processus après un arrêt. Si cette option n’est pas sélectionnée, vous pouvez choisir d’appliquer les modifications à l’aide de l’élément « Appliquer les modifications du code » dans le menu Déboguer.  
  
 **Signaler le code périmé \(natif uniquement\)**  
 Obtenez des avertissements concernant le code périmé.  
  
 **Autoriser la précompilation \(natif uniquement\)**  
 La précompilation est autorisée.  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)