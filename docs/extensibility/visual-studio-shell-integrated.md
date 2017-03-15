---
title: "Visual Studio Shell (intégré) | Documents Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (intégré)
Le shell Visual Studio intégré inclut l’environnement de développement intégré (IDE), le débogueur et l’intégration du contrôle de code source. Aucun langage de programmation n’est incluse. Toutefois, l’environnement intégré offre une infrastructure qui vous permet d’ajouter des langages de programmation.  
  
 Le shell Visual Studio intégré est en fait une combinaison de l’interpréteur de commandes de Visual Studio isolé plus une installation supplémentaire qui incluent des composants spécifiques de l’interface intégrée.  L’application de l’interface intégrée doit inclure à la fois le package redistribuable shell isolé à partir de [Package redistribuable Microsoft Visual Studio Shell (isolé)](http://go.microsoft.com/fwlink/?LinkId=616022) , ainsi que le package redistribuable du shell intégré de [Package redistribuable Microsoft Visual Studio Shell (intégré)](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Avant de pouvoir accéder les packages redistribuables shell isolé et intégré, vous devrez remplir un questionnaire client brève.  Après avoir complété l’enquête, vous allez être redirigé vers une page de Visual Studio se connecter avec des liens de téléchargement de package redistribuable.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio se connecter sous le **programmes | VISUAL STUDIO 2015 intégré et SHELL isolé** onglet.  
  
 Si vous installez votre application d’environnement intégré sur le même ordinateur qu’une version complète de Visual Studio, les composants de votre application seront intégrées directement dans Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Fonctionnalités dans l’environnement intégré  
  
|||  
|-|-|  
|Zone fonctionnelle|Fonctionnalité|  
|Prise en charge linguistique|-Aucun|  
|IDE|<ul><li>Paramètres<br /><br /> <ul><li>Créer des paramètres</li><li>Importation et exportation de paramètres</li><li>Réinitialiser les paramètres</li></ul></li><li>**Boîte à outils** intégration</li><li>**Liste des tâches** intégration</li><li>Intégration de l’aide</li><li>**Options** boîte de dialogue</li><li>Gestion des polices et couleurs</li><li>**Sortie** fenêtre</li><li>**Commande** fenêtre</li><li>Gestion des fenêtres</li><li>Commandes, les menus et les combinaisons de touches</li><li>Exécution de langage spécifique au domaine (DSL)</li></ul>|  
|Système de projet et les Types de projets|-Les solutions et les dossiers de solution<br />: Gestionnaire de configuration de solution<br />: Gestion des éléments<br />-Solutions projet unique et plusieurs projets<br />-Le Concepteur d’applications (propriétés du projet simplifié)<br />-Ajouter une référence Web<br />-Ajouter une référence de Service<br />Projet unique<br />: Types de projets de site Web<br />: Projets d’application web|  
|Build|-Étapes de génération personnalisée dans l’IDE<br />-Précompilation pour la protection des droits de propriété intellectuelle (IP)<br />: Signature de code<br />     MSBuild|  
|Éditeur|-Code navigation outils (recherche unifiée, définition de la source, l’héritage)<br />: Navigation dans le code<br />-IntelliSense<br />: Balises actives<br />-La refactorisation<br />-Tabulation<br />-Filtrage IntelliSense<br />-   **Définition de code** fenêtre|  
|Designer|-Concepteur Windows Presentation Foundation<br />-Windows Forms Designer<br />-Web concepteur et un éditeur HTML|  
|Données|-   **Explorateur de serveurs** (simplifié : données uniquement). Voir la remarque 1.<br />-   **Sources de données** fenêtre<br />-Ensemble des contrôles de données<br />: Éditeur XML<br />-Données lier à la source de données locale (. MDF ou. MDB)<br />-Lier des données objet<br />-Lier des données service Web<br />-Lier des données au serveur de base de données locale<br />-Lier des données au serveur de base de données distante<br />-Outils DDL pour les données distantes<br />-   **Explorateur de serveurs** extensibilité ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] exemples)|  
|Débogueur|-Débogage local. Voir la Remarque 2.<br />-Le débogage managé<br />-Débogage local<br />-Attacher au processus local<br />-Attacher au processus à distance<br />-Délégué anonyme<br />: Domaines d’application<br />-Débogage ASPX<br />: Attributs<br />-Interrompre pendant l’évaluation de fonction<br />-Points d’arrêt<br />: Contraintes de point d’arrêt<br />-La pile des appels<br />-   **Commande** fenêtre<br />-Débogage inter-threads<br />-Conseils de données<br />-Visualiseur de données<br />-Prise en charge du débogueur pour les assistants de débogage managés (MDA)<br />-Prise en charge du débogueur pour le transfert de type<br />-Prise en charge DTEEvents OTB<br />-JMC exécution pas à pas<br />-Test AppID (DBGCLR) du débogueur<br />: Profil du débogueur<br />-Outils et les options du débogueur<br />-Itérateur débogage<br />-Évaluation de l’expression au moment du design<br />-C# évaluateur d’Expression<br />-Le code machine<br />-Modifier & Continuer<br />-Windows d’évaluateur expression (espion, variables locales, automatique)<br />: Assistance de l’exception<br />: Exceptions<br />-L’exécution<br />-Génériques<br />-Mise en route de source appropriée<br />HPC débogage de Cluster<br />-Multilingue à un débogage intégré<br />-Débogage interOp<br />-Débogage juste-à-temps<br />-Débogage local<br />-Le débogage managé<br />-Contrôle manuel (fenêtre de processus)<br />-Mémoire<br />-Prise en charge miniDump<br />-Modules<br />-Plusieurs processus de débogage<br />-Natif débogage<br />-Nouveau support de moteur de débogage<br />-Débogage de code optimisé<br />-Windows sortie de filtrage<br />-Processus d’hébergement pour le débogage managé<br />-Processus<br />-Espion express<br />: Registres<br />-Les registres de pile<br />-Débogage distant<br />-Valeurs de retour<br />: Débogage de script<br />-Prise en charge du service source<br />-Sécurité<br />Côte-à-côte<br />-SQL<br />: Serveur de symboles<br />: Points de trace<br />-Thread<br />-Visualisations<br />-Extensible débogueur Stylesheet Language Transformations (XSLT)|  
|prise en charge&64; bits|-débogage 64 bits pour le code natif et managé, toutes les langues<br />-x64 natif prend en charge|  
|Contrôle de Code source (SCC)|-Intégration du contrôle de code source de base. Voir la remarque 3.<br />-Les outils et les options de vérification|  
|Extensibilité|-Consommer des composants de packages VS et MEF|  
  
## <a name="notes"></a>Remarques  
  
#### <a name="1-data-tools"></a>1. Outils de données  
 L’environnement intégré inclut des outils de développement de base de données telles que la prise en charge d’extension de données et simplifié **l’Explorateur de solutions**. Toutefois, SQL Server Express, SQL Reporting et Crystal Reports ne sont pas inclus dans l’environnement intégré.  
  
#### <a name="2-debugging-support"></a>2. Prise en charge du débogage  
 L’environnement intégré inclut le même moteur de débogage qui est inclus dans la version Community de Visual Studio. Le moteur de débogage inclut le débogueur commun pour le code managé, ainsi que des fonctionnalités connexes, telle que l’exécution, l’attachement, définissez un point d’arrêt, modifier et continuer. Toutefois, le moteur de débogage ne prend pas en charge le débogage de la base de données SQL Server.  
  
 Bien que prise en charge pour le débogage natif est inclus dans le package de base de débogueur, vous ne pouvez pas étendre pour prendre en charge des langues supplémentaires.  
  
#### <a name="3-source-code-control-integration"></a>3. Intégration du contrôle de Code source  
 L’environnement intégré fournit des API pour l’implémentation du contrôle de code source (SCC) et pour fournir le contrôle de source commune basée sur MSSCCI composants d’intégration.  
  
 Intégration du contrôle de code source n’est pas une fonction standard de l’édition professionnelle de Visual Studio, intégration du contrôle de code source est fournie dans l’environnement intégré.  
  
#### <a name="4-build-support"></a>4. Support de build  
 L’environnement intégré prend en charge de génération. Vous pouvez trouver des informations sur les builds dans le [MSBuild référence](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Fonctionnalités non incluses dans l’environnement intégré  
 Voici une liste des fonctionnalités qui ne sont pas inclus dans l’environnement intégré :  
  
-   Concepteur de classes  
  
-   [Protection preEmptive - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Fonctionnalités de langage  
  
-   VSHost  
  
-   Aucune langue de Visual Studio ou leurs modèles de projet associés ou les modèles d’élément de projet, sont inclus dans l’environnement intégré. Aucune implémentation spécifique à la langue d’autres fonctionnalités n’est incluses, exemple Visual Basic des extraits de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de présentation de Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)
