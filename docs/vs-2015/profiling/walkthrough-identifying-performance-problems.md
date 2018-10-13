---
title: 'Procédure pas à pas : Identification des problèmes de performances | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be81688429d6a7d9d8d2cc5fa3e1e1a5662d1263
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274480"
---
# <a name="walkthrough-identifying-performance-problems"></a>Procédure pas à pas : Identification des problèmes de performances
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment profiler une application pour identifier les problèmes de performances.  
  
 Dans cette procédure pas à pas, vous allez voir comment profiler une application managée et utiliser l’échantillonnage et l’instrumentation pour isoler et identifier les problèmes de performances de l’application.  
  
 Dans cette procédure pas à pas, vous allez suivre les étapes suivantes :  
  
-   Profiler une application à l’aide de la méthode d’échantillonnage  
  
-   Analyser les résultats d’un profilage échantillonné pour rechercher et résoudre un problème de performances  
  
-   Profiler une application à l’aide de la méthode d’instrumentation  
  
-   Analyser les résultats d’un profilage instrumenté pour rechercher et résoudre un problème de performances  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Compréhension intermédiaire de C#.  
  
-   Une copie de l’[exemple PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Pour utiliser les informations fournies par le profilage, il est préférable de disposer des informations de symboles de débogage.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilage à l’aide de la méthode d’échantillonnage  
 L’échantillonnage est une méthode de profilage par laquelle le processus en question est périodiquement interrogé pour déterminer la fonction active. Les données résultantes fournissent le nombre de fois que la fonction était sur la pile des appels quand le processus en question a été échantillonné.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Pour profiler une application à l’aide de la méthode d’échantillonnage  
  
1.  Ouvrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] avec les privilèges d'administrateur. L’exécution en tant qu’administrateur est obligatoire pour le profilage.  
  
2.  Ouvrez la solution PeopleTrax.  
  
     La solution PeopleTrax alimente l’Explorateur de solutions.  
  
3.  Définissez la configuration de projet sur **Version finale**.  
  
     Vous devez utiliser une version Release pour détecter les problèmes de performances dans votre application. Une version Release est recommandée pour le profilage, car une version Debug comporte des informations supplémentaires compilées qui peuvent nuire aux performances et n’illustrent pas avec précision les problèmes de performances.  
  
4.  Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.  
  
     L’Assistant Performance apparaît.  
  
5.  Vérifiez que **Échantillonnage de l’UC (recommandé)** est sélectionné, puis cliquez sur **Suivant**.  
  
6.  Dans **Quelle application voulez-vous cibler pour le profilage ?**, sélectionnez PeopleTrax, puis cliquez sur **Suivant**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] génère le projet et commence à profiler l’application. La fenêtre d’application **PeopleTrax** s’affiche.  
  
7.  Cliquez sur **Get People** (Obtenir des personnes).  
  
8.  Cliquez sur **Exporter les données**.  
  
     Le Bloc-notes s’ouvre et affiche un nouveau fichier qui contient les données exportées à partir de **PeopleTrax**.  
  
9. Fermez le Bloc-notes, puis l’application **PeopleTrax**.  
  
     Le profileur génère un fichier de profilage de données (\*.vsp), indique le nom du fichier dans la section Rapports de la fenêtre Explorateur de performances et charge automatiquement la vue **Résumé** du fichier de données dans la fenêtre principale de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Pour analyser les résultats d’un profilage échantillonné  
  
1.  La vue Résumé affiche une chronologie de l’utilisation du processeur au cours du profilage, la liste **Chemin réactif** qui représente la branche de l’arborescence des appels de l’application qui était la plus active et une liste des **fonctions faisant le plus de travail individuel** qui indique les fonctions qui ont été le plus échantillonnées pendant l’exécution de code dans leur propre corps.  
  
     Examinez la liste **Chemin réactif** et notez que la méthode PeopleNS.People.GetNames représente la fonction PeopleTrax la plus proche de la fin de la liste. Sa position en fait un bon candidat pour l’analyse. Cliquez sur le nom de la fonction pour afficher les détails de GetNames dans la vue **Informations relatives à la fonction**.  
  
2.  La vue **Informations relatives à la fonction** contient deux fenêtres. La fenêtre de la distribution des coûts fournit une vue graphique du travail effectué par la fonction, du travail effectué par les fonctions qu’elle a appelées et de la contribution des fonctions ayant appelé la fonction au nombre d’instances qui ont été échantillonnées. Vous pouvez modifier la fonction qui détient le focus dans la vue en cliquant sur un nom de fonction. Par exemple, vous pouvez cliquer sur PeopleNS.People.GetPeople pour faire de GetPeople la fonction sélectionnée.  
  
     La fenêtre **Affichage du code de fonction** montre le code source de la fonction s’il est disponible et met en surbrillance les lignes les plus coûteuses dans la fonction sélectionnée. Quand GetNames est sélectionnée, vous pouvez voir qu’elle lit une chaîne dans les ressources d’application, puis utilise un <xref:System.IO.StringReader> pour ajouter chaque ligne de la chaîne à un <xref:System.Collections.ArrayList>. Il n’existe aucun moyen évident d’optimiser cette fonction.  
  
3.  Étant donné que PeopleNS.People.GetPeople est le seul appelant de GetNames, cliquez sur GetPeople dans la fenêtre de la distribution des coûts pour examiner son code. Cette méthode retourne une <xref:System.Collections.ArrayList> d’objets PersonInformationNS.PersonInformation à partir des noms de personnes et d’entreprises produits par GetNames. Toutefois, GetNames est appelé deux fois chaque fois qu’un objet PersonInformation est créé. Comme vous pouvez le constater, vous pouvez facilement optimiser la méthode en créant les listes une seule fois au début de la méthode et en procédant à une indexation dans ces listes pendant la boucle de création de PersonInformation.  
  
4.  Une autre version de GetPeople est fournie avec l’exemple de code d’application et vous pouvez appeler la fonction optimisée en ajoutant un symbole de compilation conditionnelle aux propriétés de génération. Dans la fenêtre Explorateur de solutions, cliquez avec le bouton droit sur le projet People, puis cliquez sur **Propriétés**. Cliquez sur **Générer** dans le menu de la page des propriétés, puis tapez **OPTIMIZED_GETPEOPLE** dans la zone de texte Symboles de compilation conditionnelle. La version optimisée de GetPeople remplace la méthode d’origine dans la build suivante.  
  
5.  Réexécutez la session de performance. Dans la barre d’outils Explorateur de performances, cliquez sur **Démarrer avec le profilage**. Cliquez sur **Get People** (Obtenir des personnes), puis sur **Exporter les données**. Fermez la fenêtre du Bloc-notes qui s’affiche, puis l’application PeopleTrax.  
  
     Un nouveau fichier de données de profilage est généré et une vue **Résumé** pour les nouvelles données s’affiche dans la fenêtre principale de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
6.  Pour comparer les deux exécutions de profilage, sélectionnez les deux fichiers de données dans l’Explorateur de performances, cliquez avec le bouton droit sur les fichiers, puis cliquez sur **Comparer les rapports de performances**. Une fenêtre Rapport de comparaison s’affiche dans la fenêtre principale de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. La colonne **Différentiel** indique la modification de la valeur de performance des fonctions entre l’ancienne valeur **Ligne de base** et la nouvelle valeur **Comparaison**. Vous pouvez sélectionner les valeurs à comparer dans la liste déroulante **Colonne**. Sélectionnez **% d’échantillons inclusifs**.  
  
     Notez que les méthodes GetPeople et GetNames affichent des gains de performances considérables.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilage à l’aide de la méthode d’instrumentation  
 L’instrumentation est une méthode de profilage dans laquelle le profileur insère des fonctions de sonde dans des versions des binaires profilés spécialement générées. Les sondes collectent les informations de temporisation à l’entrée et à la sortie des fonctions dans les modules instrumentés et sur tous les sites d’appel de ces fonctions. Le processus d’instrumentation est utile pour examiner les problèmes liés aux opérations d’entrée/sortie telles que l’écriture sur le disque et la communication sur un réseau. L’instrumentation fournit des informations plus détaillées que l’échantillonnage, mais elle s’avère plus importune dans l’exécution des processus et entraîne une surcharge plus importante. En outre, les binaires instrumentés sont plus volumineux que les binaires Debug ou Release et ne sont pas destinés à être déployés.  
  
 Dans cette section de la procédure pas à pas, nous allons utiliser la méthode d’instrumentation pour découvrir davantage de code que nous pouvons optimiser dans l’application PeopleTrax que nous avons profilée. En utilisant le filtre de la chronologie de la vue Résumé, nous concentrerons notre analyse sur le scénario d’exportation de données dans notre application profilée, dans lequel la liste de personnes est écrite dans un fichier Bloc-notes.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Pour profiler une application existante à l’aide de la méthode d’instrumentation  
  
1.  Si nécessaire, ouvrez l’application PeopleTrax dans Visual Studio.  
  
     Vérifiez que vous exécutez en tant qu’administrateur et que la configuration de build de la solution est définie sur **Version finale**.  
  
2.  Dans l’Explorateur de performances, cliquez sur **Instrumentation**.  
  
3.  Dans la barre d’outils Explorateur de performances, cliquez sur **Démarrer avec le profilage**.  
  
     Le profileur génère le projet et commence à profiler l’application. La fenêtre d’application PeopleTrax s’affiche.  
  
4.  Cliquez sur **Get People** (Obtenir des personnes).  
  
     La grille de données PeopleTrax se remplit avec des données.  
  
5.  Attendez environ 10 secondes, puis cliquez sur **Exporter les données**.  
  
     Le **Bloc-notes** démarre et affiche un nouveau fichier qui contient une liste de personnes issue de l’application PeopleTrax. Le temps d’attente vous permet d’identifier plus facilement la procédure d’exportation des données pour le filtrage.  
  
6.  Fermez le **Bloc-notes**, puis l’application **PeopleTrax**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] génère un rapport de session de performance (*.vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Pour analyser les résultats d’un profilage instrumenté  
  
1.  Le graphique de chronologie de la vue **Résumé** du rapport affiche l’utilisation du processeur du programme pendant la durée du profilage. L’opération d’exportation de données doit être le plateau ou sommet élevé sur le côté droit du graphique. Nous pouvons filtrer la session de performance pour afficher et analyser uniquement les données qui ont été collectées pendant l’opération d’exportation. Cliquez sur le graphique à gauche du point auquel commence l’opération d’exportation de données. Cliquez à présent sur le côté droit de l’opération. Ensuite, cliquez sur **Filtrer par sélection** dans la liste des liens à droite de la chronologie.  
  
     L’arborescence **Chemin réactif** montre que la méthode <xref:System.String.Concat%2A> qui est appelée par la méthode PeopleTrax.Form1.ExportData consomme un pourcentage important du temps. Étant donné que **System.String.Concat** est également en haut de la liste **Fonctions exigeant le plus de travail individuel**, réduire le temps passé dans la fonction est un point d’optimisation possible.  
  
2.  Double-cliquez sur **System.String.Concat** dans une des tables de résumé pour afficher plus d’informations dans la vue Informations relatives à la fonction.  
  
3.  Vous pouvez voir que PeopleTrax.Form1.ExportData est la seule méthode qui appelle Concat. Cliquez sur **PeopleTrax.Form1.ExportData** dans la liste **Fonctions appelantes** pour sélectionner la méthode comme cible de la vue Informations relatives à la fonction.  
  
4.  Examinez la méthode dans la fenêtre Affichage du code de fonction. Notez qu’il n’y a pas d’appels littéraux à **System.String.Concat**. Par contre, il existe plusieurs utilisations de l’opérande +=, que le compilateur remplace par des appels à **System.String.Concat**. Toute modification apportée à une chaîne dans le .NET Framework entraîne l’allocation d’une nouvelle chaîne. Le .NET Framework inclut une classe <xref:System.Text.StringBuilder> qui est optimisée pour la concaténation de chaînes.  
  
5.  Pour remplacer cette zone problématique par du code optimisé, ajoutez OPTIMIZED_EXPORTDATA comme symbole de compilation conditionnelle au projet PeopleTrax.  
  
6.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet PeopleTrax, puis cliquez sur **Propriétés**.  
  
     Le formulaire des propriétés du projet PeopleTrax s’affiche.  
  
7.  Cliquez sur l’onglet **Générer**.  
  
8.  Dans la zone de texte **Symboles de compilation conditionnelle**, tapez **OPTIMIZED_EXPORTDATA**.  
  
9. Fermez le formulaire des propriétés du projet et choisissez **Enregistrer tout** quand vous y êtes invité.  
  
 Quand vous réexécuterez l’application, vous constaterez une nette amélioration des performances. Nous vous recommandons de réexécuter la session de profilage, même si les performances laissent apparaître des améliorations du point de vue de l’utilisateur. Il est important d’examiner les données après avoir résolu un problème, car le premier problème peut en masquer un autre.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues d’ensemble](../profiling/overviews-performance-tools.md)   
 [Bien démarrer](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (Format des informations de débogage)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)



