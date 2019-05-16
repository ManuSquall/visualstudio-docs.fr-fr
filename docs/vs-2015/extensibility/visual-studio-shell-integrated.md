---
title: Visual Studio Shell (intégré) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 664363740737eb72213b4818b104aa14c3667a14
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690926"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (intégré)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le shell intégré de Visual Studio inclut l’environnement de développement intégré (IDE), le débogueur et l’intégration du contrôle de code source. Aucun langage de programmation n’est inclus. Toutefois, le shell intégré offre une infrastructure qui vous permet d’ajouter des langages de programmation.  
  
 Le shell Visual Studio intégré est en fait une combinaison de l’interpréteur de commandes isolé de Visual Studio ainsi qu’une installation supplémentaire qui incluent des composants spécifiques de shell intégré.  Votre application de shell intégré doit inclure à la fois le package redistribuable shell isolé à partir de [Package redistribuable Microsoft Visual Studio Shell (isolé)](http://go.microsoft.com/fwlink/?LinkId=616022) , ainsi que le package redistribuable du shell intégré à partir de [Microsoft Visual Studio Shell (intégré) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
> Avant de pouvoir accéder les packages redistribuables du shell isolé et intégré, vous devrez remplir un petit questionnaire.  Après avoir complété l’enquête, il vous serez dirigé vers une page de connexion de Visual Studio avec des liens de téléchargement de package redistribuable.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio se connecter sous le **programmes &#124; 2015 intégré et SHELL isolé VISUAL STUDIO** onglet.  
  
 Si vous installez votre application de shell intégré sur le même ordinateur en tant qu’une version complète de Visual Studio, les composants de votre application seront intégrés directement dans Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Fonctionnalités dans le Shell intégré  
  
|||  
|-|-|  
|Domaine de fonctionnalités|Fonctionnalité|  
|Prise en charge linguistique|-None|  
|IDE|<ul><li>Paramètres<br /><br /> <ul><li>Créer des paramètres</li><li>Importation et exportation de paramètres</li><li>Réinitialiser les paramètres</li></ul></li><li>**Boîte à outils** intégration</li><li>**Liste des tâches** intégration</li><li>Intégration de l’aide</li><li>**Options** boîte de dialogue</li><li>Gestion des polices et couleurs</li><li>**Sortie** fenêtre</li><li>**Commande** fenêtre</li><li>Gestion des fenêtres</li><li>Commandes, des menus et des combinaisons de touches</li><li>Runtime de langage spécifique à un domaine (DSL)</li></ul>|  
|Système de projet et les Types de projets|-Solutions et dossiers de solution<br />-Gestionnaire de configuration de solution<br />-Gestion des éléments<br />-Solutions projet unique et plusieurs projets<br />-Concepteur d’applications (propriétés du projet simplifiée)<br />-Ajouter une référence Web<br />-Ajouter une référence de Service<br />-   Single-project<br />-Types de projets de site Web<br />: Projets d’application web|  
|Build|-Étapes de génération personnalisée dans l’IDE<br />-Précompilation pour la protection de la propriété intellectuelle (IP)<br />-Signature de code<br />     MSBuild|  
|Éditeur|-Code navigation outils (recherche unifiée, définition de la source, l’héritage)<br />-Navigation dans le code<br />-   IntelliSense<br />-   SmartTags<br />-La refactorisation<br />-Tabulation<br />-Filtrage IntelliSense<br />-   **Définition de code** fenêtre|  
|Designer|-Windows Presentation Foundation Designer<br />-Windows Forms Designer<br />-Web concepteur et l’éditeur HTML|  
|Données|-   **Explorateur de serveurs** (simplifié : données uniquement). Voir la remarque 1.<br />-   **Sources de données** fenêtre<br />-Ensemble des contrôles de données<br />-XML éditeur<br />-Données lier à la source de données locale (. MDF ou. MDB)<br />-Lier des données objet<br />-Lier des données au service Web<br />-Lier des données au serveur de base de données locale<br />-Lier des données au serveur de base de données distante<br />-Outils DDL pour les données distantes<br />-   **Explorateur de serveurs** extensibilité ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] exemples)|  
|Débogueur|-Débogage local. Voir la Remarque 2.<br />-Le débogage managé<br />-Débogage local<br />-Attacher au processus local<br />-Attacher au processus à distance<br />-Délégué anonyme<br />-Domaines d’application<br />-Débogage ASPX<br />-Attributs<br />-Interrompre pendant l’évaluation de Func<br />-Des points d’arrêt.<br />-Contraintes de point d’arrêt<br />-Pile des appels<br />-   **Commande** fenêtre<br />-Débogage inter-threads<br />-Des bulles d’informations<br />-Visualiseur de données<br />-Prise en charge du débogueur pour les Assistants Débogage managé (MDA)<br />-Prise en charge de débogueur de redirecteur de type<br />-Prise en charge DTEEvents pour OTB<br />-Exécution pas à pas JMC<br />-Test AppID (DBGCLR) du débogueur<br />-Profil de débogueur<br />-Outils et les options du débogueur<br />-Débogage d’itérateur<br />-Évaluation de l’expression au moment du design<br />(Évaluateur d’Expression C#)<br />-Le code machine<br />-Modifier & Continuer<br />-Windows d’évaluateur expression (espion, variables locales, automatique)<br />: Assistance d’exception<br />-   Exceptions<br />-   Execution<br />- Génériques<br />-Obtention de source de droite<br />-Débogage/Cluster HPC<br />-Multilingue à un débogage intégré<br />-   InterOp debugging<br />-Débogage juste-à-temps<br />-Débogage local<br />-Le débogage managé<br />-Contrôle manuel (fenêtre de processus)<br />-Mémoire<br />-Prise en charge miniDump<br />-   Modules<br />-Débogage multiprocessus<br />-Débogage natif<br />-Prise en charge du moteur débogage nouveau<br />-Débogage de code optimisé<br />-Les fenêtres de sortie filtrage<br />-Processus d’hébergement pour le débogage managé<br />-Processus<br />-   Quickwatch<br />: Inscrit<br />-Les registres dans la pile<br />-Débogage distant<br />-Valeurs de retour<br />-Débogage de script<br />-Prise en charge du service source<br />-Sécurité<br />Côte-à-côte<br />-   SQL<br />-Serveur de symboles<br />-Points de trace<br />-   Thread<br />-Visualisations<br />-Extensible débogueur Stylesheet Language Transformations (XSLT)|  
|prise en charge 64 bits|-débogage 64 bits pour le code managé et natif, toutes les langues<br />-x64 natif prend en charge|  
|Contrôle de Code source (SCC)|-Intégration de SCC de base. Voir la remarque 3.<br />-Outils et les options de vérification|  
|Extensibilité|-Consommer des composants de VSPackages et MEF|  
  
## <a name="notes"></a>Notes  
  
#### <a name="1-data-tools"></a>1. Outils de données  
 Le shell intégré inclut des outils de développement de base de données comme données d’extensibilité prise en charge et simplifié **l’Explorateur de solutions**. Toutefois, SQL Server Express, SQL Reporting et Crystal Reports ne sont pas inclus dans le shell intégré.  
  
#### <a name="2-debugging-support"></a>2. Prise en charge du débogage  
 Le shell intégré inclut le même moteur de débogage qui est inclus dans la version Community de Visual Studio. Le moteur de débogage inclut le débogueur commun pour le code managé, ainsi que les fonctionnalités associées, telle que l’exécution, joindre, définissez un point d’arrêt, modifier et continuer. Toutefois, le moteur de débogage ne prend pas en charge le débogage de la base de données SQL Server.  
  
 Bien que prise en charge pour le débogage natif est inclus dans le package de base de débogueur, vous ne pouvez pas étendre pour prendre en charge des langues supplémentaires.  
  
#### <a name="3-source-code-control-integration"></a>3. Intégration du contrôle de Code source  
 Le shell intégré fournit des API pour implémenter le contrôle de code source (SCC) et pour fournir le contrôle en fonction de MSSCCI commun source des composants d’intégration.  
  
 Bien que l’intégration du contrôle de code source n’est pas une fonction standard de l’édition professionnelle de Visual Studio, intégration du contrôle de code source est fournie dans l’interpréteur de commandes intégré.  
  
#### <a name="4-build-support"></a>4. Prise en charge de build  
 Le shell intégré prend en charge de build. Vous trouverez des informations sur les builds dans le [MSBuild référence](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Fonctionnalités non incluses dans le Shell intégré  
 Voici une liste des fonctionnalités qui ne sont pas inclus dans le shell intégré :  
  
- Concepteur de classes  
  
- PreEmptive Protection - Dotfuscator  
  
- Fonctionnalités de langage  
  
- VSHost  
  
- Aucune langue de Visual Studio ou leurs modèles de projet associé ou modèles d’élément de projet, sont inclus dans l’interpréteur de commandes intégré. Aucune implémentation spécifique à la langue d’autres fonctionnalités n’est incluses, exemple Visual Basic des extraits de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Visual Studio extension](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)