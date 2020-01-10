---
title: Shell Visual Studio (intégré) | Microsoft Docs
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
ms.openlocfilehash: 78ccba3ab8c2dda531614fa791eac3100813840a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299701"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (intégré)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le shell intégré de Visual Studio comprend l’environnement de développement intégré (IDE), le débogueur et l’intégration du contrôle de code source. Aucun langage de programmation n’est inclus. Toutefois, l’interpréteur de commandes intégré fournit une infrastructure qui vous permet d’ajouter des langages de programmation.  
  
 L’interpréteur de commandes intégré de Visual Studio est en fait une combinaison de l’interpréteur de commandes isolé de Visual Studio plus une installation supplémentaire qui inclut des composants intégrés à l’interpréteur de commandes.  Votre application shell intégrée doit inclure à la fois le package redistribuable Shell isolé de [Microsoft Visual Studio Shell (isolé) package redistribuable](https://go.microsoft.com/fwlink/?LinkId=616022) , ainsi que le package redistribuable Shell intégré de [Microsoft Visual Studio Shell (intégré) package redistribuable](https://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
> Avant de pouvoir accéder aux packages redistribuables de l’interpréteur de commandes isolé et intégré, vous serez invité à fournir une brève enquête client.  Après avoir complété l’enquête, vous serez redirigé vers une page de connexion à Visual Studio avec des liens de téléchargement de packages redistribuables.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio Connect sous l’onglet  **&#124; programmes Visual Studio 2015 intégré et environnement isolé** .  
  
 Si vous installez votre application shell intégrée sur le même ordinateur qu’une version complète de Visual Studio, les composants de votre application sont intégrés directement dans Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Fonctionnalités de l’interpréteur de commandes intégré  
  
|||  
|-|-|  
|Domaine de fonctionnalités|Composant|  
|Prise en charge linguistique|-Aucun|  
|IDE|<ul><li>Paramètres<br /><br /> <ul><li>Créer des paramètres</li><li>Importer et exporter des paramètres</li><li>Réinitialiser les paramètres</li></ul></li><li>Intégration de la **boîte à outils**</li><li>Intégration de **liste des tâches**</li><li>Intégration de l’aide</li><li>**Options** , boîte de dialogue</li><li>Gestion des polices et des couleurs</li><li>Fenêtre **sortie**</li><li>Fenêtre **commande**</li><li>Gestion des fenêtres</li><li>Commandes, menus et combinaisons de touches</li><li>Runtime de langage spécifique à un domaine (DSL)</li></ul>|  
|Système de projet et types de projets|-Solutions et dossiers de solution<br />-Gestionnaire de configuration de solution<br />-Gestion des éléments<br />-Solutions à projet unique et à projets multiples<br />-Concepteur d’applications (propriétés simplifiées du projet)<br />-Ajouter une référence Web<br />-Ajouter une référence de service<br />-Projet unique<br />-Types de projets de site Web<br />-Projets d’application Web|  
|Build|-Étapes de génération personnalisée dans l’IDE<br />-Précompilation pour la protection de la propriété intellectuelle (IP)<br />-Signature du code<br />     MSBuild|  
|Éditeur|-Outils de navigation du code (recherche unifiée, définition de la source, héritage)<br />-Navigation dans le code<br />-   IntelliSense<br />-   SmartTags<br />-Refactorisation<br />-Listing convivial<br />-Filtrage IntelliSense<br />-   la fenêtre **définition de code**|  
|Designer|-Windows Presentation Foundation designer<br />-Concepteur Windows Forms<br />-Concepteur Web et éditeur HTML|  
|Données|-   **Explorateur de serveurs** (simplifié : données uniquement). Voir la remarque 1.<br />-   la fenêtre **sources de données**<br />-Jeu complet de contrôles de données<br />-Éditeur XML<br />-Liaison de données à la source de données locale (. MDF ou. MDB<br />-Liaison de données à l’objet<br />-Liaison de données au service Web<br />-Liaison de données au serveur de base de données local<br />-Liaison de données au serveur de base de données distant<br />-Outils DDL pour les données distantes<br />-   **Explorateur de serveurs** extensibilité (exemples[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)])|  
|Débogueur|-Débogage local. Voir la remarque 2.<br />-Débogage managé<br />-Débogage local<br />-Attacher au processus local<br />-Attacher au processus distant<br />-Délégué anonyme<br />-Domaines d’application<br />-Débogage ASPX<br />-Attributs<br />-Break pendant Func-eval<br />-Points d’arrêt<br />-Contraintes de point d’arrêt<br />-CallStack<br />fenêtre de **commande** -   <br />-Débogage inter-threads<br />-Conseils sur les données<br />-Visualiseur de données<br />-Prise en charge du débogueur pour les Assistants Débogage managé (MDA)<br />-Prise en charge du débogueur pour le redirecteur de type<br />-Prise en charge de DTEEvents pour le banc d’or<br />-UNIQUEMENT mon code pas à pas<br />-Test AppID du débogueur (DBGCLR)<br />-Profil du débogueur<br />-Outils et options du débogueur<br />-Iterator de débogage<br />-Évaluation d’une expression au moment du design<br />- C# Évaluateur d’expression<br />-Code machine<br />-Modifier & continuer<br />-Fenêtres de l’évaluateur d’expression (espion, variables locales, automatique)<br />-Helper d’exception<br />-   Exceptions<br />-Exécution<br />- Génériques<br />-Obtention de la source de droite<br />-HPC/débogage de cluster<br />-Le débogage multilingue intégré<br />-Débogage d’interopérabilité<br />-Débogage juste-à-temps<br />-Débogage local<br />-Débogage managé<br />-Contrôle manuel (fenêtre processus)<br />-Mémoire<br />-Prise en charge du minidump<br />-Modules<br />-Débogage multiprocessus<br />-Débogage natif<br />-Nouvelle prise en charge du moteur de débogage<br />-Débogage de code optimisé<br />-Filtrage Windows en sortie<br />-Processus d’hébergement pour le débogage managé<br />-Processus<br />-   Quickwatch<br />-Registres<br />-S’inscrit dans la pile<br />-Débogage à distance<br />-Valeurs de retour<br />-Débogage de script<br />-Prise en charge du service source<br />-Sécurité<br />-Côte à côte<br />-SQL<br />-Serveur de symboles<br />-Points de trace<br />-Thread<br />-Visualisations<br />-Débogueur XSLT (Extensible Stylesheet Language Transformations)|  
|Support 64 bits|-débogage 64 bits pour le code managé et le code natif, tous les langages<br />-prise en charge native x64|  
|Contrôle de code source (SCC)|-Intégration SCC de base. Voir la remarque 3.<br />-Vérification des outils et options|  
|Extensibilité|-Utiliser les VSPackages et les composants MEF|  
  
## <a name="notes"></a>Remarques  
  
#### <a name="1-data-tools"></a>1. outils de données  
 L’environnement intégré comprend des outils de développement de base de données tels que la prise en charge de l’extensibilité des données et le **Explorateur de solutions**simplifié. Toutefois, les rapports SQL Server Express, SQL Reporting et Crystal ne sont pas inclus dans l’interpréteur de commandes intégré.  
  
#### <a name="2-debugging-support"></a>2. prise en charge du débogage  
 L’interpréteur de commandes intégré inclut le même moteur de débogage que celui inclus dans la version Community de Visual Studio. Le moteur de débogage comprend le débogueur commun pour le code managé, ainsi que des fonctionnalités associées, telles que l’exécution, l’attachement, la définition d’un point d’arrêt, la modification et la poursuite, etc. Toutefois, le moteur de débogage ne prend pas en charge le débogage de base de données SQL Server.  
  
 Bien que la prise en charge du débogage natif soit incluse dans le package du débogueur de base, vous ne pouvez pas l’étendre pour prendre en charge des langages supplémentaires.  
  
#### <a name="3-source-code-control-integration"></a>3. intégration du contrôle de code source  
 L’interpréteur de commandes intégré fournit des API permettant d’implémenter le contrôle de code source (SCC) et de fournir les composants d’intégration de contrôle de code source MSSCCI basés sur MSSCCI.  
  
 Bien que l’intégration SCC ne soit pas une fonctionnalité standard de l’édition Pro de Visual Studio, l’intégration SCC est fournie dans l’interpréteur de commandes intégré.  
  
#### <a name="4-build-support"></a>4. prise en charge des builds  
 L’interpréteur de commandes intégré assure la prise en charge de la Build. Vous pouvez trouver des informations sur les builds dans la [référence MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Fonctionnalités non incluses dans l’interpréteur de commandes intégré  
 Voici une liste des fonctionnalités qui ne sont pas incluses dans l’interpréteur de commandes intégré :  
  
- Concepteur de classes  
  
- PreEmptive Protection - Dotfuscator  
  
- Fonctionnalités de langage  
  
- VSHost  
  
- Aucun langage Visual Studio ou les modèles de projet ou d’élément de projet associés ne sont inclus dans l’interpréteur de commandes intégré. Aucune implémentation spécifique à une langue d’autres fonctionnalités n’est incluse, par exemple Visual Basic des extraits de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’extension de Visual Studio](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)