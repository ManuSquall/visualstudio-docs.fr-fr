---
title: "Visual Studio Shell (int&#233;gr&#233;) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fonctionnalités de l'interface en mode intégré de Visual Studio"
  - "Shell (Visual Studio), les fonctionnalités en mode intégré"
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Visual Studio Shell (int&#233;gr&#233;)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le shell Visual Studio intégré inclut l'environnement de développement intégré \(IDE\), le débogueur et l'intégration du contrôle de code source. Aucun langage de programmation n'est incluse. Toutefois, l'environnement intégré offre une infrastructure qui vous permet d'ajouter des langages de programmation.  
  
 Le shell Visual Studio intégré est en fait une combinaison de l'interpréteur de commandes de Visual Studio isolé plus une installation supplémentaire qui incluent des composants spécifiques de l'interface intégrée.  L'application de l'interface intégrée doit inclure à la fois le package redistribuable shell isolé à partir de [Package redistribuable Microsoft Visual Studio Shell \(isolé\)](http://go.microsoft.com/fwlink/?LinkId=616022) ainsi que le package redistribuable du shell intégré de [Package redistribuable Microsoft Visual Studio Shell \(intégré\)](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Avant de pouvoir accéder les packages redistribuables shell isolé et intégré, vous devrez remplir un questionnaire client brève.  Après avoir complété l'enquête, vous allez être redirigé vers une page de Visual Studio se connecter avec des liens de téléchargement de package redistribuable.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio se connecter sous le **programmes &#124; VISUAL STUDIO 2015 intégré et SHELL isolé** onglet.  
  
 Si vous installez votre application d'environnement intégré sur le même ordinateur qu'une version complète de Visual Studio, les composants de votre application seront intégrées directement dans Visual Studio.  
  
## Fonctionnalités dans l'environnement intégré  
  
|||  
|-|-|  
|Zone fonctionnelle|Fonctionnalité|  
|Prise en charge linguistique|-   None|  
|IDE|<ul><li>Paramètres<br /><br /> <ul><li>Créer des paramètres</li><li>Importation et exportation de paramètres</li><li>Réinitialiser les paramètres</li></ul></li><li>**Boîte à outils** intégration</li><li>**Liste des tâches** intégration</li><li>Intégration de l'aide</li><li>**Options** boîte de dialogue</li><li>Gestion des polices et couleurs</li><li>**Sortie** fenêtre</li><li>**Commande** fenêtre</li><li>Gestion des fenêtres</li><li>Commandes, les menus et les combinaisons de touches</li><li>Exécution de langage spécifique au domaine \(DSL\)</li></ul>|  
|Système de projet et les Types de projets|-   Solutions et dossiers de solution<br />-   Gestionnaire de configuration de solution<br />-   Gestion des éléments<br />-   Solutions de projet unique et plusieurs projets<br />-   Concepteur d'applications \(propriétés du projet simplifié\)<br />-   Ajouter une référence web<br />-   Ajouter une référence de service<br />-   Projet unique<br />-   Types de projets de site Web<br />-   Projets d'application Web|  
|Build|-   Étapes de génération personnalisée dans l'IDE<br />-   Précompilation pour la protection des droits de propriété intellectuelle \(IP\)<br />-   Signature de code<br />     MSBuild|  
|Éditeur|-   Code de navigation outils \(recherche unifiée, définition de la source, l'héritage\)<br />-   Navigation dans le code<br />-   IntelliSense<br />-   Balises actives<br />-   Refactorisation<br />-   Tabulation<br />-   Filtrage IntelliSense<br />-   **Définition de code** fenêtre|  
|Designer|-   Concepteur Windows Presentation Foundation<br />-   Concepteur Windows Forms<br />-   Concepteur de sites Web et l'éditeur HTML|  
|Données|-   **Explorateur de serveurs** \(simplifié : données uniquement\). Voir la remarque 1.<br />-   **Des Sources de données** fenêtre<br />-   Ensemble des contrôles de données<br />-   Éditeur XML<br />-   Lier des données à la source de données locale \(. MDF ou. MDB\)<br />-   Liaison de données à l'objet<br />-   Liaison de données au service Web<br />-   Lier des données au serveur de base de données locale<br />-   Lier des données au serveur de base de données distante<br />-   Outils DDL pour les données distantes<br />-   **Explorateur de serveurs** extensibilité \([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] exemples\)|  
|Débogueur|-   Le débogage local. Voir la Remarque 2.<br />-   Débogage managé<br />-   Débogage local<br />-   Attacher à des processus locaux<br />-   Attacher au processus à distance<br />-   Délégué anonyme<br />-   Domaines d'application<br />-   Débogage ASPX<br />-   Attributs<br />-   Interrompre pendant l'évaluation de fonction<br />-   Points d’arrêt<br />-   Contraintes de point d'arrêt<br />-   Pile des appels<br />-   **Commande** fenêtre<br />-   Débogage inter\-threads<br />-   Info\-bulles<br />-   Visualiseur de données<br />-   Prise en charge pour les assistants de débogage managés \(MDA\) du débogueur<br />-   Prise en charge du débogueur pour le transfert de type<br />-   Prise en charge DTEEvents OTB<br />-   Exécution pas à pas JMC<br />-   Test de l'AppID \(DBGCLR\) du débogueur<br />-   Profil du débogueur<br />-   Options et outils de débogage<br />-   Itérateur de débogage<br />-   Évaluation d'expression au moment du design<br />-   Évaluateur d'Expression c\#<br />-   Code Machine<br />-   Modifier & Continuer<br />-   Fenêtres évaluateur d'expression \(espion, variables locales, automatique\)<br />-   Assistance de l'exception<br />-   Exceptions<br />-   Exécution<br />-   Génériques<br />-   Mise en route de la source de droite<br />-   Débogage de Cluster HPC<br />-   Débogage multilingue intégré<br />-   Débogage d'interopérabilité<br />-   Le débogage juste\-à\-temps<br />-   Débogage local<br />-   Débogage managé<br />-   Contrôle manuel \(fenêtre de processus\)<br />-   Mémoire<br />-   Prise en charge miniDump<br />-   Modules<br />-   Débogage de plusieurs processus<br />-   Débogage en natif<br />-   Nouvelle prise en charge moteur de débogage<br />-   Débogage de code optimisé<br />-   Filtrage des fenêtres de sortie<br />-   Processus d'hébergement pour le débogage managé<br />-   Processus<br />-   Espion express<br />-   Registres<br />-   Registres de pile<br />-   Débogage distant<br />-   Valeurs de retour<br />-   Débogage de script<br />-   Prise en charge du service de source<br />-   Sécurité<br />-   Côte à côte<br />-   SQL<br />-   Serveur de symboles<br />-   Points de trace<br />-   Thread<br />-   Visualisations<br />-   Extensible débogueur Stylesheet Language Transformations \(XSLT\)|  
|prise en charge 64 bits|-   déboguer le code managé et natif, toutes les langues pour 64 bits<br />-   prise en charge x 64 natif|  
|Contrôle de Code source \(SCC\)|-   Intégration de contrôle de code source de base. Voir la Remarque 3.<br />-   Outils et options de vérification|  
|Extensibilité|-   Consommer des composants MEF et les packages VS|  
  
## Notes  
  
#### 1. Outils de données  
 L'environnement intégré inclut des outils de développement de base de données telles que la prise en charge d'extension de données et simplifié **l'Explorateur de solutions**. Toutefois, SQL Server Express, SQL Reporting et Crystal Reports ne sont pas inclus dans l'environnement intégré.  
  
#### 2. Prise en charge du débogage  
 L'environnement intégré inclut le même moteur de débogage qui est inclus dans la version Community de Visual Studio. Le moteur de débogage inclut le débogueur commun pour le code managé, ainsi que des fonctionnalités connexes, telle que l'exécution, l'attachement, définissez un point d'arrêt, modifier et continuer. Toutefois, le moteur de débogage ne prend pas en charge le débogage de la base de données SQL Server.  
  
 Bien que prise en charge pour le débogage natif est inclus dans le package de base de débogueur, vous ne pouvez pas étendre pour prendre en charge des langues supplémentaires.  
  
#### 3. Intégration du contrôle de Code source  
 L'environnement intégré fournit des API pour l'implémentation du contrôle de code source \(SCC\) et pour fournir le contrôle de source commune basée sur MSSCCI composants d'intégration.  
  
 Intégration du contrôle de code source n'est pas une fonction standard de l'édition professionnelle de Visual Studio, intégration du contrôle de code source est fournie dans l'environnement intégré.  
  
#### 4. Support de build  
 L'environnement intégré prend en charge de génération. Vous pouvez trouver des informations sur les builds dans le [MSBuild Reference](../msbuild/msbuild-reference.md).  
  
## Fonctionnalités non incluses dans l'environnement intégré  
 Voici une liste des fonctionnalités qui ne sont pas inclus dans l'environnement intégré :  
  
-   Concepteur de classes  
  
-   DotFuscator préventive  
  
-   Fonctionnalités de langage  
  
-   VSHost  
  
-   Aucune langue de Visual Studio ou leurs modèles de projet associés ou les modèles d'élément de projet, sont inclus dans l'environnement intégré. Aucune implémentation spécifique à la langue d'autres fonctionnalités n'est incluses, exemple Visual Basic des extraits de code.  
  
## Voir aussi  
 [Vue d’ensemble de l’extension de Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)