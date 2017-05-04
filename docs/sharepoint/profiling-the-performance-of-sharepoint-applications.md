---
title: "Profilage des performances des applications SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Profiling.SilverlightWebPartOnly"
  - "VS.SharePointTools.Profiling.DotNetTrustLevel"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "test des performances (développement SharePoint dans Visual Studio)"
  - "profilage (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, test de performances"
  - "développement SharePoint dans Visual Studio, profilage"
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Profilage des performances des applications SharePoint
  Si vos applications SharePoint fonctionnent lentement ou de manière inefficace, vous pouvez utiliser les fonctionnalités de profilage dans Visual Studio pour identifier le code problématique et d'autres éléments.  En utilisant la fonctionnalité de test de charge, vous pouvez déterminer comment une application SharePoint fonctionne en situation de stress, lorsque de nombreux utilisateurs accès simultanément à l'application par exemple.  En exécutant des tests de performances de site Web, vous pouvez mesurer le comportement de l'application sur le Web.  En utilisant des tests d'interface utilisateur codés, vous pouvez vérifier si l'application SharePoint toute entière, y compris son interface utilisateur, fonctionne correctement.  Lorsque vous utilisez ces tests ensemble, ils peuvent vous aider à identifier des problèmes de performances avant que vous ne déployiez votre application.  
  
## Vue d'ensemble des outils de profilage  
 Le profilage fait référence au processus d'observation et d'enregistrement du comportement de performance de votre application pendant son exécution.  En profilant votre application, vous pouvez découvrir des problèmes tels que des goulots d'étranglement, un code inefficace et des problèmes d'allocation de mémoire, qui font que les applications s'exécutent lentement ou utilisent trop de mémoire.  Par exemple, vous pouvez utiliser le profilage pour identifier les zones réactives de votre code, qui sont des segments de code souvent appelés qui peuvent ralentir les performances globales de votre application.  Lorsque vous avez identifié les zones réactives, vous pouvez souvent les optimiser ou les supprimer.  
  
 Vous pouvez utiliser plusieurs outils de profilage dans l'environnement de développement intégré \(IDE\) pour identifier et localiser ces genres de problèmes de performances.  Ces outils fonctionnent de la même manière pour les projets SharePoint que pour d'autres types de projets Visual Studio.  L'Assistant Performance des outils de profilage vous guide dans la création d'une session de performance qui utilise les tests que vous spécifiez.  Une session de performance est un ensemble de données de configuration utilisé pour collecter les données de performance d'une application, avec les résultats d'une ou de plusieurs exécutions de profilage.  Les sessions de performance sont stockées dans votre dossier de projet, et vous pouvez les afficher dans l'**Explorateur de performances**.  Pour plus d'informations, consultez [Fonctionnement des méthodes de profilage](../profiling/understanding-performance-collection-methods.md).  
  
 Après avoir créé et exécuté une analyse de profil sur votre application, un rapport fournit des détails sur ses performances.  Ce rapport peut inclure des éléments tels qu'un graphique de l'utilisation du processeur au fil du temps, une pile d'appels hiérarchique de fonction, ou une arborescence des appels.  Le contenu exact du rapport peut varier, selon le type de test que vous exécutez, tel que l'échantillonnage ou l'instrumentation.  Pour plus d'informations, consultez [Vue d'ensemble des rapports d'outils de profilage](http://go.microsoft.com/fwlink/?LinkId=224689).  
  
## Processus de session de performance  
 Pour profiler une application, vous devez commencer par utiliser Assistant Performance des outils de profilage pour créer une session de performance.  Dans la barre de menus, choisissez **Analyser** , **Lancer l'Assistant Performance**.  Au dernières étapes de l'Assistant, vous entrez les informations requises pour votre session de performance, comme la méthode de profil que vous souhaitez ainsi que l'application que vous souhaitez profiler.  Pour plus d'informations, consultez [Comment : profiler un site Web ou une application Web à l'aide de l'Assistant Performance \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=224692).  Sinon, vous pouvez utiliser les options de ligne de commande pour définir et exécuter une session de performance.  Pour plus d'informations, consultez [Utilisation des outils de profilage à partir de la ligne de commande](http://go.microsoft.com/fwlink/?LinkId=224703).  Si vous souhaitez configurer manuellement chaque aspect d'une session de performance, consultez [Comment : Créer manuellement des sessions de performance avec les outils de profilage \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=224691).  Vous pouvez également créer une session de performance à partir d'un test unitaire en ouvrant, dans la fenêtre **Résultats des tests**, le menu contextuel du test unitaire, puis en choisissant **Créer une session de performance**.  
  
 Après avoir installé une session de performance, la configuration de la session est enregistrée, le serveur est configuré pour fournir des données de profilage et l'application est exécutée.  En utilisant l'application, les données de performance sont écrites dans un fichier journal.  Les sessions de performance sont répertoriées dans l'**Explorateur de performances** sous le dossier **Cibles**.  Lorsqu'une session de performance se termine, son rapport apparaît dans le dossier **Rapports** de l'**Explorateur de performances**.  Pour afficher le rapport, ouvrez\-le dans l'**Explorateur de performances**.  Pour afficher ou configurer les propriétés d'une session de performance, ouvrez le menu contextuel dans **Explorateur de performances**, puis sélectionnez **Propriétés**.  Pour plus d'informations sur les propriétés spécifiques d'une session de performance, consultez [Configuration des sessions de performance pour les outils de profilage \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=224694).  Pour plus d'informations sur l'interprétation des résultats d'une session de performance, consultez [Analyse des données des outils de profilage \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=224704).  
  
## Test de contrainte  
 Vous pouvez analyser les performances liées aux contraintes de vos applications en créant des tests de charge et des tests de performances de site Web dans Visual Studio Ultimate.  Lorsque vous créez un test de charge dans Visual Studio, vous spécifiez une combinaison de facteurs, appelée scénario, pour tester votre application.  Ces facteurs incluent le modèle de charge, le modèle de combinaison de tests, la combinaison de tests, la combinaison de réseaux et la combinaison de navigateurs Web.  Les scénarios de tests de charge peuvent contenir des tests unitaires et des tests de performances de site Web.  
  
 Figure 1 : Exemple de résultats du test de charge  
  
 ![Exécution de la vue des graphiques du test de charge](../sharepoint/media/load-webgraphs.png "Exécution de la vue des graphiques du test de charge")  
  
 Les tests des performances de site Web simulent la façon dont un utilisateur final peut interagir avec une application SharePoint.  Les tests des performances de site Web sont créés en enregistrant des requêtes HTTP dans une session de navigateur ou à l'aide de l'**Enregistreur de test de performances de site Web**.  Les requêtes Web apparaissent dans l'**éditeur de test de performances de site Web** à la fin de la session de navigateur.  Vous pouvez ensuite déboguer les résultats dans l'**Afficheur des résultats des tests de performances de site Web**.  Vous pouvez également générer manuellement des tests de performances de site Web à l'aide de l'**Éditeur de tests de performances de site Web**.  
  
## Test des interfaces utilisateur  
 Les tests codés d'IU contrôlent automatiquement votre application SharePoint via son interface utilisateur \(IU\).  Ces tests couvrent les contrôles d'interface utilisateur, tels que des boutons et des menus, afin de vérifier qu'ils fonctionnent correctement.  Ce genre de test est particulièrement utile si la validation ou une autre logique est effectuée dans l'interface utilisateur, par exemple dans une page Web.  Vous pouvez également utiliser les tests codés de l'interface utilisateur pour automatiser les tests manuels.  Vous créez des tests codés de l'interface utilisateur pour vos applications SharePoint de la même façon que vous créez des tests pour d'autres types d'applications.  Pour plus d'informations, consultez [Test des applications SharePoint 2010 avec des tests codés de l'interface utilisateur](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Walkthrough: Profiling a SharePoint Application](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Montre comment exécuter une analyse de profil d'échantillonnage sur une application SharePoint.|  
|[Create and run a load test](http://msdn.microsoft.com/fr-fr/7041cbcf-9ab1-4579-98ff-8f296aeaded4)|Décrit comment créer des tests de charge, qui vous aident à effectuer des tests de contrainte sur les applications SharePoint.|  
|[Creating and Editing Web Performance Tests](http://msdn.microsoft.com/fr-fr/8bf5f2a7-c693-47d6-9282-5946480151dc)|Décrit comment créer des tests de performances de site Web, qui vous aident à simuler comment un utilisateur interagit avec votre site SharePoint sur le Web.|  
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|Décrit comment rechercher les erreurs de logique dans votre code à l'aide de tests unitaires.|  
|[Test des applications SharePoint 2010 avec des tests codés de l'interface utilisateur](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Décrit comment tester l'interface utilisateur de vos applications SharePoint.|  
  
## Voir aussi  
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Test de l'application](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Améliorer la qualité du code](../test/improve-code-quality.md)  
  
  