---
title: Mémoire JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
ms.assetid: 78f8532b-7b4e-4b50-b8b7-68ca0926dd4e
caps.latest.revision: 54
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2341e9cf0ca1494d8dad79cd521c283c2c23a06
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "51798935"
---
# <a name="javascript-memory"></a>Mémoire JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'analyseur de mémoire JavaScript est disponible dans Visual Studio pour vous aider à comprendre l'utilisation de la mémoire et à rechercher les fuites de mémoire dans vos applications du Windows Store générées pour Windows en JavaScript. Les applications prises en charge comprennent les applications du Windows Phone Store et du Windows Store.  
  
 L'analyseur de mémoire JavaScript peut effectuer les opérations suivantes :  
  
- Vous aider à détecter rapidement les problèmes d'utilisation de la mémoire dans votre application en mettant en évidence les données les plus pertinentes.  
  
   Ces données sont disponibles dans des résumés d'instantanés qui montrent les différences entre deux instantanés et fournissent des liens vers des vues plus détaillées.  
  
- Fournir des vues des dominateurs, des types et des racines pour aider à isoler les problèmes.  
  
- Réduire les informations ne pouvant pas être exploitées dans les données de tas JavaScript.  
  
   Les objets qui ne sont pas créés directement dans votre code d'application sont automatiquement exclus. Vous pouvez également filtrer les données par nom d'objet.  
  
  Pour vous guider dans le processus d’identification d’une fuite de mémoire dans une application, consultez [Procédure pas à pas : Recherche d’une fuite de mémoire (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
  Dans cette rubrique :  
  
  [Exécuter l'analyseur de mémoire JavaScript](#Run)   
  [Vérifier l'utilisation de la mémoire](#Check)   
  [Isolate a memory leak](#Isolate)   
  [Visualiser le résumé dynamique d'utilisation de la mémoire](#LiveMemory)   
  [View a snapshot summary](#SnapshotSummary)   
  [Visualiser les détails de l'instantané](#SnapshotDetails)   
  [Visualiser une comparaison d'instantanés](#SnapshotDiff)   
  [Afficher les objets par dominateur](#FoldObjects)   
  [Filtrer les données par identificateur](#Filter)   
  [Rechercher un objet dans l'arborescence des objets](#ShowInRootsView)   
  [Visualiser les références aux objets partagés](#References)   
  [Afficher les objets intégrés](#BuiltInValues)   
  [Enregistrer les fichiers de diagnostic de session](#Save)   
  [Associate source code with memory usage data](#JSConsoleCommands)   
  [Conseils pour identifier les problèmes de mémoire](#Tips)  
  
##  <a name="Run"></a> Exécuter l'analyseur de mémoire JavaScript  
 Vous pouvez utiliser l’analyseur de mémoire lorsque vous avez une application du Windows Store ouverte dans Visual Studio ou installée sur un ordinateur exécutant [!INCLUDE[win8](../includes/win8-md.md)] ou version ultérieure.  
  
#### <a name="to-run-the-memory-analyzer"></a>Pour exécuter l'analyseur de mémoire  
  
1.  Ouvrez Visual Studio.  
  
2.  Si vous exécutez l'application à partir de Visual Studio, dans la barre d'outils **Standard** , dans la liste **Démarrer le débogage** , choisissez la cible de débogage de votre projet : un émulateur Windows Phone ou, pour une application du Windows Store, un **Ordinateur local**, un **Simulateur**ou un **Ordinateur distant**.  
  
     Pour plus d’informations sur ces options, consultez [Exécuter des applications à partir de Visual Studio](../debugger/run-store-apps-from-visual-studio.md).  
  
3.  Dans la barre de menus, choisissez **Déboguer****Profileur de performances...**  
  
     Par défaut, le projet de démarrage actif est analysé. Si vous souhaitez modifier la cible d'analyse, sélectionnez **Modifier la cible**.  
  
     ![Modifier la cible de l’analyse](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Les options suivantes sont disponibles pour la cible d'analyse :  
  
    -   **Projet de démarrage**. Analyse le projet de démarrage en cours. Si vous exécutez l'application sur un ordinateur distant, vous devez sélectionner cette option, qui est l'option par défaut.  
  
    -   **Application en cours d'exécution**. Permet de sélectionner une application du Windows Store dans une liste d'applications en cours d'exécution. Vous ne pouvez pas utiliser cette option lorsque vous exécutez l'application sur un ordinateur distant.  
  
         Utilisez cette option pour analyser l'utilisation de la mémoire des applications en cours d'exécution sur votre ordinateur lorsque vous n'avez pas accès au code source.  
  
    -   **Application installée**. Permet de sélectionner une application du Windows Store installée à analyser. Vous ne pouvez pas utiliser cette option lorsque vous exécutez l'application sur un ordinateur distant.  
  
         Utilisez cette option pour analyser l'utilisation de la mémoire des applications installées sur votre ordinateur lorsque vous n'avez pas accès au code source. Cette option s'avère également utile lorsque vous voulez uniquement analyser l'utilisation de la mémoire d'une application en dehors de votre propre développement d'applications.  
  
4.  Dans **Outils disponibles**, cochez la case **Mémoire JavaScript** , puis sélectionnez **Démarrer**.  
  
5.  Lorsque vous démarrez l'analyseur de mémoire, une fenêtre Contrôle de compte d'utilisateur peut vous demander l'autorisation d'exécuter Visual Studio ETW Collector.exe. Cliquez sur **Oui**.  
  
     Interagissez avec l'application pour tester les scénarios appropriés d'utilisation de la mémoire et examinez le graphique de mémoire, comme décrit dans les sections suivantes.  
  
6.  Basculez vers Visual Studio en appuyant sur Alt+Tab.  
  
7.  Pour afficher les données que l'analyseur de mémoire rassemble, sélectionnez **Prendre un instantané du tas**. Consultez [View a snapshot summary](#SnapshotSummary) plus loin dans cette rubrique.  
  
##  <a name="Check"></a> Vérifier l'utilisation de la mémoire  
 Vous pouvez essayer d'identifier les fuites de mémoire grâce à différentes vues de l'analyseur de mémoire JavaScript. Si vous pensez que votre application rencontre des fuites de mémoire, consultez [Isolate a memory leak](#Isolate) pour une suggestion de flux de travail.  
  
 Utilisez les vues suivantes pour aider à identifier les fuites de mémoire dans une application :  
  
-   [Visualiser le résumé dynamique d'utilisation de la mémoire](#LiveMemory). Utilisez le graphique d'utilisation de la mémoire pour rechercher des augmentations soudaines de l'utilisation de la mémoire ou une utilisation de la mémoire en constante augmentation résultant d'actions particulières. Utilisez la vue du résumé dynamique d'utilisation de la mémoire pour prendre des instantanés du tas. Les instantanés apparaissent sous forme de collection sous le graphique d'utilisation de la mémoire.  
  
    > [!TIP]
    >  Vous verrez un pic d'activité dans l'utilisation de la mémoire en prenant un instantané. Utilisez les résumés des instantanés pour obtenir une indication plus exacte de l'évolution.  
  
-   [View a snapshot summary](#SnapshotSummary). Vous pouvez consulter les informations résumées relatives aux instantanés pendant ou après une session de profilage de mémoire. Utilisez les résumés des instantanés pour les lier aux détails d'un instantané et aux vues comparées des instantanés.  
  
    > [!TIP]
    >  En général, les vues comparées des instantanés fournissent les informations les plus utiles sur les fuites de mémoire.  
  
-   [Visualiser les détails de l'instantané](#SnapshotDetails). Affiche des données détaillées relatives à l'utilisation de la mémoire pour un instantané unique.  
  
-   [Visualiser une comparaison d'instantanés](#SnapshotDiff). Affiche les valeurs comparées pour différents instantanés. Ces vues affichent les différences de taille d'objets et de nombre d'objets.  
  
##  <a name="Isolate"></a> Isolate a memory leak  
 La procédure suivante présente un flux de travail qui peut vous aider à utiliser l'analyseur de mémoire JavaScript plus efficacement. Ces étapes peuvent s'avérer utiles si vous pensez que votre application rencontre une fuite de mémoire. Pour vous guider dans le processus d’identification d’une fuite de mémoire dans une application, consultez [Procédure pas à pas : Recherche d’une fuite de mémoire (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
1. Ouvrez votre application dans Visual Studio.  
  
2. Exécutez l'analyseur de mémoire JavaScript. Pour plus d'informations, consultez [Exécuter l'analyseur de mémoire JavaScript](#Run).  
  
3. Exécutez votre application via le scénario que vous souhaitez tester. Par exemple, le scénario peut impliquer une mutation DOM importante, durant le chargement d'une page spécifique ou au démarrage de l'application.  
  
4. Répétez le scénario 1 à 4 fois de plus.  
  
   > [!TIP]
   >  En répétant le scénario de test plusieurs fois, vous contribuez à garantir le filtrage du travail d'initialisation dans les résultats.  
  
5. Basculez vers Visual Studio (appuyez sur Alt+Tab).  
  
6. Prenez un instantané du tas de base en sélectionnant **Prendre un instantané du tas**.  
  
    L'illustration suivante montre un exemple d'instantané de ligne de base :  
  
    ![Instantané de ligne base](../profiling/media/js-mem-leak-workflow-baseline.png "JS_Mem_Leak_Workflow_Baseline")  
  
   > [!TIP]
   >  Pour exercer un contrôle plus précis de la synchronisation des instantanés, utilisez la commande [Associate source code with memory usage data](#JSConsoleCommands) dans votre code.  
  
7. Revenez à votre application et répétez le scénario que vous testez (une seule fois).  
  
8. Basculez vers Visual Studio et prenez un deuxième instantané.  
  
9. Revenez à votre application et répétez le scénario que vous testez (une seule fois).  
  
10. Basculez vers Visual Studio et prenez un troisième instantané.  
  
     L'illustration suivante montre l'exemple d'un deuxième et d'un troisième instantané.  
  
     ![Deuxième et troisième instantanés](../profiling/media/js-mem-leak-workflow.png "JS_Mem_Leak_Workflow")  
  
     En prenant un instantané de référence, un deuxième instantané, puis un troisième dans ce flux de travail, vous pouvez filtrer plus facilement les changements qui ne sont pas associés à des fuites de mémoire. Par exemple, certains changements peuvent être prévus, comme la mise à jour des en-têtes et des pieds de page sur une page, ce qui génère des changements dans l'utilisation de la mémoire sans que cela soit lié à des fuites de mémoire.  
  
11. À partir du troisième instantané, choisissez un lien vers l'une des vues comparées :  
  
    - Taille différentielle de tas (lien de gauche sous la taille du tas). Le texte du lien indique la différence entre la taille du tas de l'instantané actuel et la taille du tas de l'instantané précédent.  
  
    - Nombre différentiel d'objets (lien de droite sous le nombre d'objets). Le texte du lien indique deux valeurs (par exemple + 1858 / -1765) : la première valeur est le nombre de nouveaux objets ajoutés depuis l’instantané précédent. La deuxième valeur est le nombre d’objets supprimés depuis l’instantané précédent.  
  
      Ces liens ouvrent une vue comparée des détails d'instantané pour les types du tas, par ordre de taille retenue ou de nombre d'objets, selon le lien que vous avez ouvert.  
  
12. Choisissez l'une des options suivantes relatives au filtre **Portée** pour faciliter l'identification des problèmes d'utilisation de la mémoire :  
  
    -   **Objets créés à partir de l'instantané #2**.  
  
    -   **Objets ajoutés entre les instantanés n° 2 et n° 3**  
  
    > [!TIP]
    >  Utilisez la vue filtrée des objets restants du précédent instantané pour analyser les fuites de mémoire. Par exemple, si le nombre différentiel d'objets est 205 / -195, cette vue montre les 10 objets restants. Ces derniers peuvent correspondre à des fuites de mémoire.  
  
     L'illustration suivante montre une vue comparée des objets restants de l'instantané n° 2.  
  
     ![Vue de la comparaison des instantanés affichant les types](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
     Dans l'illustration précédente, nous voyons qu'il reste deux objets de l'instantané précédent. Cherchez à savoir si ce comportement est attendu pour votre application. Si ce n'est pas le cas, il peut s'agir d'une fuite de mémoire.  
  
13. Pour voir à quel endroit les objets des vues comparées sont enracinés à l'objet global, ce qui les empêche de faire l'objet d'un garbage collection, ouvrez le menu contextuel d'un objet, puis choisissez **Afficher en vue racine**. Un grand nombre d'objets peuvent être conservés en mémoire dans la mesure où ils sont référencés par un objet unique (ou quelques objets) enracinés à l'objet global.  
  
14. S'il existe trop d'objets dans la vue des objets restants, essayez d'isoler davantage la période pendant laquelle la fuite de mémoire se produit, puis prenez à nouveau trois instantanés. Pour isoler davantage la fuite de mémoire, utilisez [Associate source code with memory usage data](#JSConsoleCommands), un [Associate source code with memory usage data](#JSConsoleCommands), et les autres données d'utilisation de la mémoire disponibles dans l'analyseur de mémoire.  
  
##  <a name="LiveMemory"></a> Visualiser le résumé dynamique d'utilisation de la mémoire  
 La vue Résumé dynamique d'utilisation de la mémoire fournit un graphique d'utilisation de la mémoire pour l'application en cours d'exécution et la collection de toutes les vignettes de résumé des instantanés. Dans cette vue, vous pouvez effectuer des tâches de base, comme effectuer des instantanés, analyser des informations de résumé et accéder à d'autres vues. Quand vous arrêtez de collecter des données, le graphique de la mémoire disparaît et vous voyez uniquement la vue [View a snapshot summary](#SnapshotSummary) .  
  
 Le graphique de mémoire affiche une vue active de la mémoire de processus de l'application. Il indique les octets privés, la mémoire native et le tas JavaScript. Le graphique de mémoire est une vue déroulante de la mémoire de processus. Voici à quoi elle ressemble :  
  
 ![Graphique de mémoire Analyseur de mémoire JavaScript](../profiling/media/js-mem-memory-graph.png "JS_Mem_Memory_Graph")  
  
 Si vous avez ajouté des marques utilisateur au code de l'application (consultez [Associate source code with memory usage data](#JSConsoleCommands)), un triangle inversé apparaît dans le graphique d'utilisation de la mémoire pour indiquer quand cette section de code est atteinte.  
  
 Une partie de la mémoire présentée dans le graphique de la mémoire est allouée par le runtime JavaScript. Vous ne pouvez pas contrôler l'utilisation de cette mémoire dans votre application. L'utilisation de la mémoire représentée dans le graphique augmente lorsque vous effectuez votre premier instantané, puis augmente de façon minimale à chaque instantané suivant.  
  
##  <a name="SnapshotSummary"></a> View a snapshot summary  
 Pour effectuer un instantané de l'état actuel de l'utilisation de la mémoire de votre application, sélectionnez **Prendre un instantané du tas** dans le graphique de la mémoire. Une vignette de résumé de l'instantané, qui apparaît à la fois dans le résumé dynamique d'utilisation de la mémoire (pendant l'exécution de l'application) et dans le résumé de l'instantané (une fois l'application arrêtée), fournit des informations sur le tas JavaScript et des liens vers des informations plus détaillées. Si vous effectuez deux instantanés ou plus, un instantané fournit des informations supplémentaires par comparaison de ses données avec celles de l'instantané précédent.  
  
> [!NOTE]
>  L'analyseur de mémoire JavaScript force un garbage collection avant chaque instantané. Cela permet de garantir une meilleure cohérence des résultats entre les différentes exécutions.  
  
 Voici un exemple de résumé de l'instantané lorsque vous effectuez plusieurs instantanés.  
  
 ![Résumé de l’instantané](../profiling/media/js-mem-snapshot-summary.png "JS_Mem_Snapshot_Summary")  
  
 Le résumé de l'instantané inclut :  
  
-   Titre et horodatage de l'instantané.  
  
-   Nombre de problèmes potentiels (marqués par une icône bleue d'informations). Ce nombre, le cas échéant, identifie les problèmes potentiels de mémoire, tels que des nœuds qui ne sont pas joints au DOM. Ce nombre est lié à la vue Types de l'instantané, qui est triée par type de problème pour mettre en évidence les problèmes potentiels. Une info-bulle affiche la description du problème.  
  
-   Taille du tas. Ce nombre comprend les éléments DOM et les objets que le moteur d'exécution JavaScript ajoute au tas JavaScript. La taille du tas est liée à la vue Types de l'instantané.  
  
-   Taille différentielle de tas. Cette valeur indique la différence entre la taille du tas de l'instantané actuel et celle de l'instantané précédent. Cette valeur est suivie d'une flèche rouge vers le haut en cas d'augmentation de la mémoire ou d'une flèche verte vers le bas en cas de diminution de la mémoire. Si la taille du tas n'a pas changé entre les instantanés, le texte **Aucune modification** s'affiche à la place d'un nombre. Pour le premier instantané, le texte **Ligne de base**s'affiche. La taille différentielle de tas est liée à la vue Types de la comparaison des instantanés.  
  
-   Nombre d'objets. Ce nombre indique uniquement les objets créés dans votre application et exclut les objets intégrés créés par le runtime JavaScript. Le nombre d'objets est lié à la vue Types des détails d'un instantané.  
  
-   Nombre différentiel d'objets. Il indique deux valeurs : la première valeur est le nombre de nouveaux objets ajoutés depuis l’instantané précédent. La deuxième valeur est le nombre d’objets supprimés depuis l’instantané précédent. Par exemple, l'illustration montre que 1 859 objets ont été ajoutés et 1 733 objets ont été supprimés depuis l'instantané n°1. Cette information est suivie d'une flèche rouge vers le haut si le nombre total d'objets a augmenté ou d'une flèche verte vers le bas s'il a diminué. Si le nombre d'objets n'a pas changé, le texte **Aucune modification** s'affiche à la place d'un nombre. Pour le premier instantané, le texte **Ligne de base**s'affiche. Le nombre différentiel d'objets est lié à la vue Types de la comparaison d'instantanés.  
  
-   Capture d'écran lors de la prise de l'instantané.  
  
##  <a name="SnapshotDetails"></a> Visualiser les détails de l'instantané  
 Vous pouvez visualiser des informations détaillées sur l'utilisation de la mémoire pour chaque instantané dans les vues de détails d'un instantané.  
  
 Dans la vue Résumé de l'instantané, sélectionnez un lien pour afficher les détails de l'instantané. Par exemple, le lien de la taille du tas ouvre les détails de l'instantané avec la vue Types ouverte par défaut.  
  
 Cette illustration montre la vue Types dans les détails de l'instantané, avec les données d'utilisation de la mémoire triées par taille de retenue.  
  
 ![Vue des détails de l’instantané affichant des problèmes potentiels](../profiling/media/js-mem-snapshot-details.png "JS_Mem_Snapshot_Details")  
  
 Dans la vue des détails d'un instantané, vous pouvez passer en revue les données d'utilisation de la mémoire par type, racine ou dominateur, en sélectionnant une option dans la barre d'outils :  
  
- **Types**. Indique le nombre d'instances et la taille totale des objets sur le tas, regroupés par type d'objet. Par défaut, ceux-ci sont triés par le nombre d'instances.  
  
  > [!TIP]
  >  En règle générale, les vues comparées des types sur le tas d'objets représentent les vues les plus utiles pour identifier une fuite de mémoire. Ces vues fournissent un filtre **Portée** qui permet d'identifier les objets restants.  
  
- **Racines**. Montre une vue hiérarchique des objets, des objets racine jusqu'aux références enfants. Par défaut, les nœuds enfants sont triés sur la colonne de la taille de retenue, en ordre décroissant.  
  
- **Dominators**. Affiche une liste d'objets sur le tas qui ont des références exclusives à d'autres objets. Les dominators sont triés par taille de retenue.  
  
  > [!TIP]
  >  Lorsque vous supprimez un dominator de la mémoire, vous libérez toute la mémoire que l'objet retient. Pour quelques applications, la vue Dominators peut aider à clarifier les tailles de mémoire retenues, car vous pouvez analyser la chaîne de référence d'objets complète.  
  
  Les trois vues montrent des types de valeur semblables, notamment :  
  
- **Identificateur(s)**. Nom qui identifie le mieux l'objet. Par exemple, pour des éléments HTML, les détails de l'instantané montrent la valeur de l'attribut ID, le cas échéant.  
  
- **Type**. Type de l'objet (par exemple, élément de lien HTML ou élément div).  
  
- **Taille**. Taille de l'objet, à l'exclusion de la taille des objets référencés.  
  
- **Taille de retenue**. Somme de la taille de l'objet et de la taille de tous les objets enfants n'ayant pas d'autres parents. Pour des raisons pratiques, il s'agit de la quantité de mémoire retenue par l'objet. De ce fait, si vous supprimez l'objet, vous libérez la quantité de mémoire spécifiée.  
  
- **Nombre**. Nombre d'instances de l'objet. Cette valeur s'affiche uniquement dans la vue Types.  
  
##  <a name="SnapshotDiff"></a> Visualiser une comparaison d'instantanés  
 Dans l'analyseur de mémoire JavaScript, vous pouvez comparer un instantané à l'instantané précédent dans les vues comparées des instantanés.  
  
 Dans la vue du résumé des instantanés, vous pouvez afficher les informations de comparaison des instantanés en sélectionnant la taille de tas comparée ou les liens du nombre d'objets comparé après deux ou plusieurs instantanés.  
  
 Vous pouvez afficher des informations différentielles sur les types, les racines et les dominateurs. La comparaison des instantanés donne des informations, par exemple les objets ajoutés au tas entre les deux instantanés.  
  
 Cette illustration montre la vue Types dans une comparaison d'instantanés.  
  
 ![Vue de la comparaison des instantanés affichant les types](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
 Dans la fenêtre de comparaison des instantanés, les vues Dominators, Types et Roots sont les mêmes que dans la fenêtre [Visualiser les détails de l'instantané](#SnapshotDetails) . La comparaison d'instantanés affiche les mêmes informations que les détails de l'instantané, avec en outre les valeurs supplémentaires suivantes :  
  
- **Diff. taille**. Différence entre la taille de l'objet dans l'instantané actuel et sa taille dans l'instantané précédent, à l'exclusion de la taille des objets référencés.  
  
- **Diff. taille de retenue**. Différence entre la taille de retenue de l'objet dans l'instantané actuel et sa taille de retenue dans l'instantané précédent. La taille de retenue inclut la taille de l'objet et la taille de tous ses objets enfants n'ayant pas d'autres parents. Pour des raisons pratiques, la taille de retenue est la quantité de mémoire retenue par l'objet. De ce fait, si vous supprimez l'objet, vous libérez la quantité de mémoire spécifiée.  
  
  Pour filtrer les informations différentielles entre les instantanés, choisissez l'un des filtres **Portée** en haut des vues différentielles.  
  
- **Objets créés à partir de l’instantané n°\<numéro>**. Ce filtre montre les différences entre les objets ajoutés au tas et retirés du tas par rapport à l'instantané de base et l'instantané précédent. Par exemple, si le résumé des instantanés montre +205 / -195 dans le nombre d'objets, ce filtre indique les dix objets qui ont été ajoutés, mais pas supprimés.  
  
  > [!TIP]
  >  Pour afficher les informations les plus utiles dans ce filtre, suivez les étapes décrites dans [Isolate a memory leak](#Isolate).  
  
- **Objets ajoutés entre les instantanés n° \<numéro> et n° \<numéro>**. Ce filtre montre tous les objets ajoutés au tas à partir de l'instantané précédent.  
  
- **Tous les objets de l’instantané n° \<numéro>**. Ce paramètre de filtre ne filtre aucun objet du tas.  
  
  Pour afficher les références d’objet qui ne correspondent pas au filtre **Portée**, sélectionnez **Afficher les références incohérentes** dans la liste des paramètres ![Liste déroulante des paramètres dans l’analyseur de mémoire](../profiling/media/js-mem-settings.png "JS_Mem_Settings") située dans l’angle supérieur droit du volet. Si vous activez ce paramètre, les références incohérentes sont affichées en texte gris.  
  
> [!TIP]
>  Nous recommandons de suivre les étapes décrites dans [Isolate a memory leak](#Isolate) puis d'utiliser le filtre **Portée** des objets restants pour identifier plus facilement les objets qui présentent une fuite de mémoire.  
  
##  <a name="FoldObjects"></a> Afficher les objets par dominateur  
 Dans les vues Types et Dominators, vous pouvez choisir d'afficher les objets dans leurs dominateurs (il s'agit de la vue par défaut sous l'onglet Dominators). Quand cette vue est sélectionnée, seuls les dominateurs sont affichés dans la vue de niveau supérieur des objets. (Les objets qui sont des descendants d'objets non globaux sont masqués de la vue de niveau supérieur.) Pour certaines applications, cela peut montrer plus précisément les objets qui sont la cause d'une fuite de mémoire en réduisant le volume de données.  
  
 Pour basculer la vue des objets par dominateur, choisisse le bouton **Plier les objets par dominateur** . ![Repli d’objets dans leurs dominateurs](../profiling/media/js-mem-fold-objects.png "JS_Mem_Fold_Objects")  
  
 Pour plus d'informations sur les dominateurs, consultez [Visualiser les détails de l'instantané](#SnapshotDetails).  
  
##  <a name="Filter"></a> Filtrer les données par identificateur  
 Dans les vues Dominators et Types, vous pouvez exclure des données en recherchant des identificateurs spécifiques. Pour rechercher un identificateur, tapez simplement son nom dans la zone de texte **Filtre de l'identificateur** dans la partie supérieure droite. Lorsque vous commencez la saisie, les identificateurs qui ne contiennent pas les caractères saisis sont exclus.  
  
 Chaque vue possède son propre filtre, de sorte que le filtre n'est pas conservé lorsque vous basculez vers une autre vue.  
  
##  <a name="ShowInRootsView"></a> Rechercher un objet dans l'arborescence des objets  
 Dans les vues Types et Dominators, vous pouvez voir la relation entre un objet particulier et l'objet `Global` . Les objets enracinés à l'objet `Global` ne font pas l'objet d'un garbage collection. Vous pouvez rechercher facilement un objet connu dans la vue Racines, sans avoir besoin d'effectuer une recherche dans l'arborescence d'objets `Global` . Pour ce faire, ouvrez le menu contextuel pour un objet dans la vue Dominators ou Types, puis sélectionnez **Afficher en vue racine**.  
  
##  <a name="References"></a> Visualiser les références aux objets partagés  
 Dans les vues Types et Dominators, le volet inférieur contient une liste de références d'objet qui indique les références partagées. Lorsque vous sélectionnez un objet dans le volet supérieur, la liste des références d'objet répertorie tous les objets qui pointent sur cet objet.  
  
> [!NOTE]
>  Les références circulaires sont indiquées par un astérisque (*) et une info-bulle, et ne peuvent pas être développées. Dans le cas contraire, cela vous empêcherez de parcourir l'arborescence et d'identifier les objets qui retiennent de la mémoire.  
  
 Si vous souhaitez obtenir une aide supplémentaire pour identifier les objets équivalents, choisissez **Afficher les ID d’objet** dans la liste des paramètres ![Liste déroulante des paramètres dans l’analyseur de mémoire](../profiling/media/js-mem-settings.png "JS_Mem_Settings") située dans l’angle supérieur droit du volet supérieur. Cette option affiche les ID d'objet en regard des noms d'objet dans la liste **Identificateur(s)** (les ID apparaissent dans toutes les vues, pas seulement dans la liste des références d'objet). Les objets qui possèdent le même ID sont des références partagées.  
  
 L'illustration suivante montre la liste des références d'objet pour un élément sélectionné avec des ID affichés.  
  
 ![Références d’objets avec affichage des ID](../profiling/media/js-mem-shared-refs.png "JS_Mem_Shared_Refs")  
  
##  <a name="BuiltInValues"></a> Afficher les objets intégrés  
 Par défaut, les vues Dominators et Types affichent uniquement les objets que vous créez dans votre application. Cela vous aide à exclure les informations superflues et à isoler les problèmes liés à l'application. Cependant, il peut parfois être utile d'afficher tous les objets générés par le runtime JavaScript pour votre application.  
  
 Pour afficher ces objets, choisissez **Afficher les éléments intégrés** dans la liste des paramètres ![Liste déroulante des paramètres dans l’analyseur de mémoire](../profiling/media/js-mem-settings.png "JS_Mem_Settings") située dans l’angle supérieur droit du volet.  
  
##  <a name="Save"></a> Enregistrer les fichiers de diagnostic de session  
 Les résumés d'instantanés de diagnostic et les vues de détails qui leur sont associées sont enregistrés en tant que fichiers .diagsession. L'**Explorateur de solutions** affiche les sessions de diagnostic précédentes dans le dossier Sessions de diagnostic. Dans l' **Explorateur de solutions**, vous pouvez ouvrir les sessions précédentes, ou supprimer ou renommer des fichiers.  
  
##  <a name="JSConsoleCommands"></a> Associate source code with memory usage data  
 Pour mieux isoler la section de code qui a un problème de mémoire, utilisez les méthodes suivantes :  
  
- Recherchez les noms de classe et les ID des éléments DOM dans les vues de détails et les vues comparées.  
  
- Recherchez les valeurs de chaîne dans les vues de détails et les vues comparées qui peuvent être associées à votre code source.  
  
- Utilisez la commande [Rechercher un objet dans l'arborescence des objets](#ShowInRootsView) pour remonter dans l'arborescence d'objets. Cela peut vous aider à identifier le code source associé.  
  
- Ajoutez les commandes de l'analyseur de mémoire à votre code source.  
  
  Vous pouvez utiliser les commandes suivantes dans votre code source :  
  
- `console.takeHeapSnapshot` prend un instantané du tas qui s'affiche dans l'analyseur de mémoire JavaScript. Cette commande est l'une des [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
- `performance.mark` définit une marque utilisateur (triangle inversé) qui apparaît dans la chronologie du graphique de mémoire, dans la vue du résumé, pendant que l'application est en cours d'exécution. Cette commande accepte un argument de chaîne qui décrit l'événement et apparaît sous la forme d'une info-bulle dans le graphique de mémoire. Cette description ne doit pas dépasser 100 caractères.  
  
> [!TIP]
>  Utilisez `console.takeHeapSnapshot` pour accélérer l'analyse lorsque vous répétez les scénarios d'utilisation de la mémoire.  
  
 Ces commandes lèvent une exception si vous les ajoutez à votre application et exécutez l'application en dehors de l'analyseur de mémoire JavaScript. Toutefois, vous pouvez tester si ces commandes existent avant des utiliser. (Ces commandes n'existent pas au début de la phase de démarrage de la session.) Pour vérifier si vous pouvez appeler `takeHeapSnapshot`sans risque, utilisez le code suivant :  
  
```javascript  
if (console && console.takeHeapSnapshot) {  
    console.takeHeapSnapshot();  
}  
```  
  
 Pour vérifier si vous pouvez appeler `performance.mark` sans risque, utilisez le code suivant :  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("message_string");  
}  
  
```  
  
 Voici un graphique de mémoire avec plusieurs marques utilisateur et l'info-bulle pour la marque utilisateur actuellement sélectionnée, pour laquelle l'argument de chaîne `performance.mark` a la valeur « data generated » (données générées) :  
  
 ![Utilisation d’une marque de profil](../profiling/media/js-mem-performance-marks.png "JS_Mem_Performance_Marks")  
  
##  <a name="Tips"></a> Conseils pour identifier les problèmes de mémoire  
  
-   Suivez le flux de travail dans [Isoler une fuite de mémoire](#Isolate) et utilisez le filtre **Objets créés à partir de l’instantané n° \<numéro>** dans une vue de comparaison pour identifier les objets qui peuvent présenter des fuites de mémoire.  
  
-   Utilisez [Rechercher un objet dans l'arborescence des objets](#ShowInRootsView) pour voir où un objet est référencé dans la hiérarchie de la mémoire. La vue Racines montre comment un objet est enraciné à l'objet global, ce qui l'empêche de faire l'objet d'un garbage collection.  
  
-   Quand il est difficile d'identifier la cause d'un problème de mémoire, utilisez les différentes vues (telles que Dominators et Types) pour rechercher des points communs, en particulier pour faciliter l'identification d'un objet (ou de quelques objets) pouvant contenir des références à de nombreux autres objets qui apparaissent dans la vue.  
  
-   Recherchez les objets qui sont conservés par inadvertance dans la mémoire après que l'utilisateur a accédé à une nouvelle page. Il s'agit d'une cause fréquente de problèmes de mémoire. Par exemple :  
  
    -   l'utilisation incorrecte de la fonction [URL.CreateObjectUrl](http://msdn.microsoft.com/library/windows/apps/hh453196.aspx) peut entraîner ce problème.  
  
    -   Certains objets peuvent fournir une méthode `dispose` et des recommandations d'utilisation. Par exemple, appelez `dispose` sur [WinJS.Binding.List](http://msdn.microsoft.com/library/windows/apps/Hh700774.aspx) si vous appelez la méthode `createFiltered` de la liste, avant de quitter une page.  
  
    -   Vous devrez peut-être supprimer un ou plusieurs détecteurs d'événements. Pour plus d'informations, consultez [View DOM event listeners](../debugger/view-dom-event-listeners.md).  
  
-   Examinez la dernière partie de [cette vidéo](http://channel9.msdn.com/Events/Build/2013/3-316) dans la conférence Build 2013 sur l'analyseur de mémoire JavaScript.  
  
-   Consultez [Gestion de la mémoire dans les applications du Windows Store](http://msdn.microsoft.com/magazine/jj651575.aspx).  
  
-   Envisagez de modifier temporairement le code pour isoler les problèmes. Vous pouvez, par exemple, décider d'effectuer les opérations suivantes :  
  
    -   Utilisez les commandes pour l'analyseur de mémoire, `console.takeSnapshot` et `performance.mark`. (Consultez [Associate source code with memory usage data](#JSConsoleCommands).)  
  
         Vous pouvez utiliser ces commandes pour favoriser l'isolement des problèmes que vous ne pouvez pas isoler en effectuant manuellement un instantané du tas.  
  
    -   Créez un objet de test et effectuez son suivi dans les vues de l'analyseur de mémoire JavaScript, telles que la vue Types. Par exemple, vous pouvez attacher un objet très volumineux à un autre objet pour voir si un objet ou un élément particulier a fait l'objet d'un garbage collection.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : recherche d’une fuite de mémoire (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md)



