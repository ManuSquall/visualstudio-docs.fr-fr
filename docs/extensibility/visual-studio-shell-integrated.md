---
redirect_url: shell/visual-studio-shell-integrated
title: "Visual Studio Shell (intégré) | Documents Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d92a6c7250e22972a2b352b74b974601ff6065c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (intégré)
Le shell intégré de Visual Studio inclut l’environnement de développement intégré (IDE), le débogueur et l’intégration du contrôle de code source. Aucun langage de programmation n’est incluse. Toutefois, l’environnement intégré fournit une infrastructure qui vous permet d’ajouter des langages de programmation.  
  
 Le shell intégré de Visual Studio est en fait une combinaison du shell isolé Visual Studio plus une installation supplémentaire qui incluent des composants spécifiques d’interpréteur de commandes intégré.  L’application de shell intégré doit inclure à la fois le package redistribuable shell isolé dans [Microsoft Visual Studio Shell (isolé) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) , ainsi que le package redistribuable shell intégré à partir de [Microsoft Visual Studio Shell (intégré) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Avant de pouvoir accéder les packages redistribuables de shell isolé et intégré, vous devrez remplir une étude brève client.  Après avoir complété l’enquête, vous allez être dirigé vers une page de connexion à Visual Studio avec des liens de téléchargement de package redistribuable.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site de Visual Studio se connecter sous le **programmes &#124; VISUAL STUDIO 2015 intégré et SHELL isolé** onglet.  
  
 Si vous installez votre application de shell intégré sur le même ordinateur qu’une version complète de Visual Studio, les composants de votre application seront intégrées directement dans Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Fonctionnalités de l’environnement intégré  
  
|||  
|-|-|  
|Domaine de fonctionnalités|Fonctionnalité|  
|Prise en charge linguistique|-Aucun|  
|IDE|<ul><li>Paramètres<br /><br /> <ul><li>Créer des paramètres</li><li>Importation et exportation de paramètres</li><li>Réinitialiser les paramètres</li></ul></li><li>**Boîte à outils** integration</li><li>**Liste des tâches** integration</li><li>Intégration de l’aide</li><li>**Options** boîte de dialogue</li><li>Gestion des polices et couleurs</li><li>**Sortie** fenêtre</li><li>**Commande** fenêtre</li><li>Gestion des fenêtres</li><li>Combinaisons de touches, les menus et commandes</li><li>Le langage spécifique à un domaine (DSL) runtime</li></ul>|  
|Système de projet et les Types de projets|-Les solutions et des dossiers solution<br />-Gestionnaire de configuration solution<br />-Gestion des éléments<br />-Solutions projet unique et à plusieurs projets<br />-Le Concepteur d’applications (propriétés du projet simplifié)<br />-Ajouter une référence Web<br />-Ajouter une référence de Service<br />Projet unique<br />-Types de projets site Web<br />: Projets d’application web|  
|Générer|-Étapes de génération personnalisée dans l’IDE<br />-Précompilation pour la protection des droits de propriété intellectuelle (IP)<br />-Signature de code<br />     MSBuild|  
|Éditeur|-Code navigation outils (recherche unifiée, définition de la source, l’héritage)<br />-Navigation dans le code<br />-IntelliSense<br />-Balises actives<br />-La refactorisation<br />-Tabulation<br />-Le filtrage IntelliSense<br />-   **Définition de code** fenêtre|  
|Designer|-Concepteur Windows Presentation Foundation<br />-Le Concepteur de formulaires Windows<br />-Web concepteur et un éditeur HTML|  
|Données|-   **L’Explorateur de serveurs** (simplifié : données uniquement). Voir la remarque 1.<br />-   **Sources de données** fenêtre<br />-Ensemble des contrôles de données<br />-XML éditeur<br />-Données lier à la source de données locale (. MDF ou. MDB)<br />-Lier les données objet<br />-Données lier au service Web<br />-Lier des données au serveur de base de données locale<br />-Lier des données au serveur de base de données distante<br />-Outils DDL pour les données distantes<br />-   **L’Explorateur de serveurs** extensibilité ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] exemples)|  
|Débogueur|-Le débogage local. Voir la Remarque 2.<br />-Le débogage managé<br />-Débogage local<br />-Attacher au processus local<br />-Attacher au processus à distance<br />-Délégué anonyme<br />-Domaines d’application<br />-Débogage ASPX<br />-Attributs<br />-Interrompre pendant l’évaluation de fonction<br />-Points d’arrêt<br />-Les contraintes point d’arrêt<br />-Pile des appels<br />-   **Commande** fenêtre<br />-Le débogage inter-threads<br />-Info-bulles<br />-Visualiseur de données<br />-Prise en charge du débogueur pour les assistants de débogage managés (MDA)<br />-Prise en charge du débogueur pour le redirecteur de type<br />-Prise en charge DTEEvents OTB<br />-JMC exécution pas à pas<br />-Le débogueur AppID test (DBGCLR)<br />-Profil de débogueur<br />-Outils et les options du débogueur<br />-Itérateur débogage<br />-Évaluation de l’expression au moment du design<br />-C# évaluateur d’Expression<br />-Le code machine<br />-Modifier & Continuer<br />-Windows d’évaluateur expression (espion, variables locales, automatique)<br />: Assistance d’exception<br />: Exceptions<br />-L’exécution<br />- Génériques<br />-Lors de l’obtention de source de droite<br />HPC débogage de Cluster<br />-Intégré du débogage de plusieurs langues<br />-Débogage interOp<br />-Le débogage juste-à-temps<br />-Débogage local<br />-Le débogage managé<br />-Contrôle manuelle (fenêtre de processus)<br />-Mémoire<br />-Prise en charge miniDump<br />: Les modules<br />-Plusieurs processus de débogage<br />-Débogage natif<br />-Nouvelle prise en charge du moteur de débogage<br />-Débogage de code optimisé<br />-Les fenêtres de sortie le filtrage<br />-Processus d’hébergement pour le débogage managé<br />-Processus<br />-Espion express<br />-Inscrit<br />-Les registres dans la pile<br />-Débogage distant<br />-Valeurs de retour<br />-Débogage de script<br />-Prise en charge du service source<br />-Sécurité<br />Côte-à-côte<br />-SQL<br />-Serveur de symboles<br />-Points de trace<br />-Threads<br />-Visualisations<br />-Débogueur de Stylesheet Language Transformations (XSLT) extensible|  
|prise en charge 64 bits|-débogage 64 bits pour le code managé et natif, toutes les langues<br />-x64 natif prend en charge|  
|Contrôle de Code source (SCC)|-Intégration du contrôle de code source de base. Voir la remarque 3.<br />-Les outils et les options de vérification|  
|Extensibilité|-Consommer des composants VSPackages et MEF|  
  
## <a name="notes"></a>Remarques  
  
#### <a name="1-data-tools"></a>1. Outils de données  
 L’environnement intégré inclut des outils de développement de base de données tels que les données d’extensibilité prise en charge et simplifié **l’Explorateur de solutions**. Toutefois, SQL Server Express, SQL Reporting et Crystal Reports ne sont pas inclus dans l’environnement intégré.  
  
#### <a name="2-debugging-support"></a>2. Prise en charge du débogage  
 L’environnement intégré inclut le même moteur de débogage qui est inclus dans la version Community de Visual Studio. Le moteur de débogage inclut le débogueur commun pour le code managé, ainsi que les fonctionnalités associées, telle que l’exécution, l’attachement, définissez un point d’arrêt, modifier et continuer. Toutefois, le moteur de débogage ne prend pas en charge le débogage de la base de données SQL Server.  
  
 Bien que prend en charge pour le débogage natif est inclus dans le package de base de débogueur, vous ne pouvez pas étendre pour prendre en charge des langues supplémentaires.  
  
#### <a name="3-source-code-control-integration"></a>3. Intégration du contrôle de Code source  
 L’environnement intégré fournit des API pour implémenter le contrôle de code source (SCC) et en fournissant le contrôle source courantes MSSCCI composants d’intégration.  
  
 Bien que l’intégration du contrôle de code source n’est pas une fonction standard de l’édition professionnelle de Visual Studio, intégration du contrôle de code source est fournie dans l’environnement intégré.  
  
#### <a name="4-build-support"></a>4. Support de build  
 L’environnement intégré fournit la prise en charge de la build. Vous trouverez des informations sur les builds dans le [MSBuild référence](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Fonctionnalités non incluses dans l’environnement intégré  
 Voici une liste des fonctionnalités qui ne sont pas inclus dans l’environnement intégré :  
  
-   Concepteur de classes  
  
-   [Protection preEmptive - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Fonctionnalités de langage  
  
-   VSHost  
  
-   Aucune langue de Visual Studio ou leurs modèles de projet associés ou les modèles d’élément de projet, sont inclus dans l’environnement intégré. Aucuns implémentations d’autres fonctionnalités spécifiques à une langue ne sont inclus, exemple Visual Basic des extraits de code.  
  
## <a name="see-also"></a>Voir aussi  
 [SDK Visual Studio](../extensibility/visual-studio-sdk.md)