---
title: "Proc&#233;dure pas &#224; pas&#160;: profilage d’applications | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, procédures pas à pas"
  - "outils d’analyse des performances, procédures pas à pas"
  - "performances, analyse"
  - "profiler des applications, procédures pas à pas"
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 53
---
# Proc&#233;dure pas &#224; pas&#160;: profilage d’applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas illustre le profilage d'une application pour identifier les problèmes de performances.  
  
 Dans cette procédure pas à pas, vous exécuterez étape par étape le processus de profilage d'une application managée et d'utilisation de l'échantillonnage et de l'instrumentation pour isoler et identifier les problèmes de performances de l'application.  
  
 Dans cette procédure pas à pas, vous exécuterez ces étapes :  
  
-   profiler une application en utilisant la méthode d'échantillonnage ;  
  
-   analyser les résultats de profilage échantillonnés pour rechercher et résoudre un problème de performance ;  
  
-   profiler une application en utilisant la méthode d'instrumentation ;  
  
-   analyser les résultats de profilage instrumentés pour rechercher et résoudre un problème de performance ;  
  
## Composants requis  
  
-   Compréhension intermédiaire de C\#.  
  
-   Copie de [PeopleTrax, exemple](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Pour utiliser les informations fournies par le profilage, il est préférable d'avoir à disposition des informations de symboles de débogage.  
  
## Profilage à l'aide de la méthode d'échantillonnage  
 L'échantillonnage est une méthode de profilage par laquelle le processus en question est périodiquement interrogé pour déterminer la fonction active.  Les données qui en résultent fournissent le nombre de fois que la fonction elle\-même était au\-dessus de la pile des appels au moment de l'échantillonnage du processus.  
  
#### Pour profiler une application à l'aide de la méthode d'échantillonnage  
  
1.  Ouvrez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] avec les privilèges d'administrateur.  L'exécution en tant qu'administrateur est obligatoire pour le profilage.  
  
2.  Ouvrez la solution PeopleTrax.  
  
     La solution PeopleTrax s'affiche à présent dans l'Explorateur de solutions.  
  
3.  Affectez au paramètre de configuration du projet l'option **Release**.  
  
     Vous devez utiliser une version Release pour détecter les problèmes de performances de votre application.  Une version Release est recommandée pour le profilage car une version Debug contient des informations complémentaires compilées qui peuvent dégrader les performances et l'empêcher d'illustrer avec exactitude les problèmes de performances.  
  
4.  Dans le menu **Analyser**, cliquez sur **Lancer l'Assistant Performance**.  
  
     L'Assistant Performance s'affiche.  
  
5.  Assurez\-vous que **Échantillonnage de l'UC \(recommandé\)** est sélectionné, puis cliquez sur **Suivant**.  
  
6.  Dans **Quelle application voulez\-vous cibler pour le profilage**, sélectionnez PeopleTrax, puis cliquez sur **Suivant**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] génère le projet et commence à profiler l'application.  La fenêtre d'application **PeopleTrax** s'affiche.  
  
7.  Cliquez sur **Get People**.  
  
8.  Cliquez sur **Exporter les données**.  
  
     Le Bloc\-notes s'ouvre et affiche un nouveau fichier qui contient les données exportées de **PeopleTrax**.  
  
9. Fermez le Bloc\-notes, puis l'application **PeopleTrax** .  
  
     Le profileur génère un fichier de données de profilage \(\*.vsp\), répertorie le nom de fichier dans la section Rapports de la fenêtre Explorateur de performances, et charge automatiquement la vue **Résumé** du fichier de données dans la fenêtre principale de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
#### Pour analyser les résultats de profilage échantillonnés  
  
1.  La vue Résumé affiche une chronologie de l'utilisation de l'unité centrale tout au long de l'exécution du profilage, la liste **Chemin réactif** qui représente la branche de l'arborescence des appels de l'application qui était la plus active et une liste **Fonctions faisant le plus de travail individuel** qui affiche les fonctions les plus échantillonnées tout en exécutant le code dans le corps de leur propre fonction.  
  
     Examinez la liste **Chemin réactif** et notez que la méthode PeopleNS.People.GetNames représente la fonction PeopleTrax la plus proche de la fin de la liste.  Sa position en fait une candidate idéale à l'analyse.  Cliquez sur le nom de fonction pour afficher des détails de GetNames dans la vue **Informations relatives à la fonction**.  
  
2.  La vue **Informations relatives à la fonction** contient deux fenêtres.  La fenêtre de distribution des coûts fournit une vue graphique du travail effectué par la fonction, du travail effectué par les fonctions qu'elle a appelées et de la contribution des fonctions qui ont appelé la fonction selon le nombre d'instances échantillonnées.  Vous pouvez modifier la fonction qui est le focus de la vue en cliquant sur un nom de fonction.  Par exemple, vous pouvez cliquer sur PeopleNS.People.GetPeople pour choisir GetPeople comme fonction sélectionnée.  
  
     La fenêtre **Affichage du code de fonction** vous montre le code source pour la fonction s'il est disponible et met en surbrillance les lignes les plus coûteuses dans la fonction sélectionnée.  Lorsque GetNames est sélectionné, vous pouvez voir que cette fonction lit une chaîne à partir des ressources d'application, puis utilise un <xref:System.IO.StringReader> pour ajouter chaque ligne dans la chaîne à un <xref:System.Collections.ArrayList>.  Il n'existe aucune façon évidente d'optimiser cette fonction.  
  
3.  Étant donné que PeopleNS.People.GetPeople est le seul appelant de GetNames, cliquez sur GetPeople dans la fenêtre de distribution des coûts pour examiner son code.  Cette méthode retourne un <xref:System.Collections.ArrayList> d'objets PersonInformationNS.PersonInformation à partir des noms de personnes et de sociétés produits par GetNames.  Toutefois, GetNames est appelé deux fois à chaque fois qu'un objet PersonInformation est créé.  Vous pouvez voir que la méthode peut être facilement optimisée en créant les listes une seule fois au démarrage de la méthode et en effectuant une indexation dans ces listes pendant la boucle de création de PersonInformation.  
  
4.  Une autre version de GetPeople est fournie avec le code d'exemple d'application et vous pouvez appeler la fonction optimisée en ajoutant un symbole de compilation conditionnelle aux propriétés de génération.  Dans la fenêtre Explorateur de solutions, cliquez avec le bouton droit sur le projet People, puis cliquez sur **Propriétés**.  Cliquez sur **Générer** dans le menu de la page de propriétés, puis tapez **OPTIMIZED\_GETPEOPLE** dans la zone de texte de symbole de compilation conditionnelle.  La version optimisée de GetPeople remplace la méthode d'origine dans la version suivante.  
  
5.  Réexécutez la session de performance.  Dans la barre d'outils de l'Explorateur de performances, cliquez sur **Démarrer avec le profilage**.  Cliquez sur **GetPeople**, puis sur **Exporter les données**.  Fermez la fenêtre Bloc\-notes qui s'affiche, puis fermez l'application People Trax.  
  
     Un nouveau fichier de données de profilage est généré, et une vue **Résumé** pour les nouvelles données s'affiche dans la fenêtre principale de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
6.  Pour comparer les deux exécutions de profilage, sélectionnez les deux fichiers de données dans l'Explorateur de performances, cliquez avec le bouton droit sur les fichiers, puis cliquez sur **Comparer les rapports de performances**.  Une fenêtre Rapport de comparaison s'affiche dans la fenêtre principale de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  La colonne **Delta** affiche la modification de la valeur de performance des fonctions qui passe de **Ligne de base** à **Élément de comparaison**.  Vous pouvez sélectionner les valeurs à comparer dans la liste déroulante **Colonne**.  Sélectionnez **% d'échantillons inclusifs**.  
  
     Notez que les méthodes GetPeople et GetNames affichent des gains de performance considérables.  
  
## Profilage à l'aide de la méthode d'instrumentation  
 L'instrumentation est une méthode de profilage dans laquelle le profileur insère des fonctions de sonde dans les versions spécialement créées des binaires profilés.  Les sondes collectent les informations de minutage à l'entrée et à la sortie de fonctions dans les modules instrumentés et dans tous les sites d'appel général de ces fonctions.  Le processus d'instrumentation est utile pour examiner les problèmes liés aux opérations d'entrée\/sortie tels que l'écriture sur le disque et la communication sur un réseau.  L'instrumentation fournit davantage d'informations détaillées que l'échantillonnage, mais elle s'avère plus importune dans l'exécution de processus et entraîne une surcharge plus importante.  Les binaires instrumentés sont également plus volumineux que les versions de débogage ou release et ne sont pas conçus pour le déploiement.  
  
 Dans cette section de la procédure pas à pas, nous utiliserons la méthode d'instrumentation permettant de découvrir davantage de code que nous pouvons optimiser dans l'application PeopleTrax que nous avons précédemment profilée.  En utilisant le filtre de la chronologie de vue Résumé, nous concentrerons notre analyse sur le scénario des données d'exportation pour notre application profilée dans laquelle la liste de personnes est écrite dans un fichier Bloc\-notes.  
  
#### Pour profiler une application existante à l'aide de la méthode d'instrumentation  
  
1.  Si nécessaire, ouvrez l'application PeopleTrax dans Visual Studio.  
  
     Assurez\-vous que vous êtes connecté en tant qu'administrateur et que la configuration de build de la solution a la valeur **Version finale**.  
  
2.  Dans l'Explorateur de performances, cliquez sur **Instrumentation**.  
  
3.  Dans la barre d'outils de l'Explorateur de performances, cliquez sur **Démarrer avec le profilage**.  
  
     Le profileur génère le projet et commence à profiler l'application.  La fenêtre d'application PeopleTrax s'affiche.  
  
4.  Cliquez sur **Get People**.  
  
     La grille de données PeopleTrax est remplie avec les données.  
  
5.  Attendez environ 10 secondes, puis cliquez sur **Exporter les données**.  
  
     Le **Bloc\-notes** démarre et affiche un nouveau fichier qui contient une liste de personnes de PeopleTrax.  L'attente vous permet d'identifier plus facilement la procédure d'exportation de données pour le filtrage.  
  
6.  Fermez le **Bloc\-notes**, puis l'application **PeopleTrax**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] génère un rapport de session de performance \(\*.vsp\).  
  
#### Pour analyser les résultats de profilage instrumentés  
  
1.  Le graphique de chronologie de la vue **Résumé** du rapport affiche l'utilisation de l'unité centrale du programme pendant toute la durée de l'exécution du profilage.  L'opération de données d'exportation doit être représentée par le plus haut sommet ou plateau dans la partie droite du graphique.  Nous pouvons filtrer la session de performance pour afficher et analyser uniquement les données collectées dans l'exportation.  Sur le graphique, cliquez à gauche du point auquel l'opération d'exportation des données commence.  Cliquez à nouveau à droite de l'opération.  Cliquez ensuite sur **Filtrer par sélection** dans la liste de liens à droite de la chronologie.  
  
     L'arborescence **Chemin réactif** montre que la méthode <xref:System.String.Concat%2A> appelée par la méthode PeopleTrax.Form1.ExportData consomme un pourcentage de temps important.  Étant donné que **System.String.Concat** se trouve également au début de la liste **Fonctions exigeant le plus de travail individuel**, la réduction du temps passé dans la fonction est un point possible d'optimisation.  
  
2.  Double\-cliquez sur **System.String.Concat** dans l'une ou l'autre des tables de résumé pour visualiser davantage d'informations dans la vue Informations relatives à la fonction.  
  
3.  Vous pouvez voir que PeopleTrax.Form1.ExportData est la seule méthode qui appelle Concat.  Cliquez sur **PeopleTrax.Form1.ExportData** dans la liste **Fonctions d'appel** pour sélectionner la méthode comme cible de la vue Informations relatives à la fonction.  
  
4.  Examinez la méthode dans la fenêtre Affichage du code de fonction.  Notez l'absence d'appels littéraux à **System.String.Concat**.  À la place, il existe de nombreuses utilisations de l'opérande \+\= que le compilateur remplace par des appels à **System.String.Concat**.  Toute modification apportée à une chaîne dans le .NET Framework provoque l'allocation d'une nouvelle chaîne.  Le .NET Framework inclut une classe <xref:System.Text.StringBuilder> qui est optimisée pour la concaténation des chaînes.  
  
5.  Pour remplacer cette source d'incident par du code optimisé, ajoutez OPTIMIZED\_EXPORTDATA comme symbole de compilation conditionnelle au projet PeopleTrax.  
  
6.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur PeopleTrax, puis cliquez sur **Propriétés**.  
  
     Le formulaire de propriétés du projet PeopleTrax s'affiche.  
  
7.  Cliquez sur l'onglet **Générer**.  
  
8.  Dans la zone de texte **Symboles de compilation conditionnelle**, tapez OPTIMIZED\_EXPORTDATA.  
  
9. Fermez le formulaire de propriétés du projet et choisissez **Enregistrer tout** lorsque vous y êtes invité.  
  
 Lorsque vous lancez à nouveau l'application, vous constaterez des améliorations au niveau des performances.  Il est recommandé de réexécuter la session de profilage, même s'il existe des améliorations au niveau des performances visibles par l'utilisateur.  Il est important de passer en revue les données après avoir résolu un problème car le premier problème peut en masquer un autre.  
  
## Voir aussi  
 [Vues d'ensemble](../profiling/overviews-performance-tools.md)   
 [Prise en main](../profiling/getting-started-with-performance-tools.md)   
 [\/Z7, \/Zi, \/ZI \(Format des informations de débogage\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)