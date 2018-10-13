---
title: Shell isolé Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e28a411ff5ef70cfd32e846edb0b70caa82c4764
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286063"
---
# <a name="visual-studio-isolated-shell"></a>Shell isolé Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le shell isolé Visual Studio vous permet de créer des applications autonomes qui peuvent s’exécuter côte à côte avec d’autres versions de Visual Studio. Il est principalement utilisée pour héberger des outils spécialisés qui peuvent utiliser les services de Visual Studio, mais également avoir une apparence personnalisée et de personnalisation. Fonctionnalités de Visual Studio et les groupes de commandes de menu peuvent être facilement activées et désactivée. Titres de l’application, les icônes d’application et les écrans de démarrage sont entièrement personnalisables. Pour obtenir la liste des fonctionnalités personnalisables, consultez [personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md).  
  
 Pour travailler avec un projet de shell isolé, vous devez installer le SDK Visual Studio. À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Pour créer une application de shell isolé, commencez par un projet Visual Studio Shell isolé. Ce projet contient tout ce dont vous avez besoin pour développer et tester votre propre application de shell isolé. Lorsque vous êtes prêt à écrire le programme d’installation qui déploie votre application, vous devez obtenir le package redistribuable du shell isolé à partir de [Package redistribuable Microsoft Visual Studio Shell (isolé)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Avant de pouvoir accéder le package redistribuable du shell isolé, vous devrez remplir un petit questionnaire.  Après avoir complété l’enquête, il vous serez dirigé vers une page de connexion de Visual Studio avec des liens de téléchargement de package redistribuable.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio se connecter sous le **programmes &#124; 2015 intégré et SHELL isolé VISUAL STUDIO** onglet.  
  
> [!NOTE]
>  Pour plus d’informations sur la façon de déployer une application shell isolée, consultez [procédure pas à pas : création d’une Application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Utilisation de l’interpréteur de commandes isolé  
 Une application de shell isolé Visual Studio a un accès complet aux services de Visual Studio et prend en charge la personnalisation spécial et personnalisation. Il existe plusieurs façons de personnaliser une application de shell isolé :  
  
-   Vous pouvez utiliser les composants des VSPackages et Managed Extensibility Framework (MEF) pour étendre une application de shell isolé, tout comme vous utiliseriez dans n’importe quelle autre extension Visual Studio. Pour plus d’informations, consultez [extension du Shell isolé](../extensibility/extending-the-isolated-shell.md).  
  
-   Pour activer ou désactiver les fonctionnalités de Visual Studio et les groupes de commandes de menu, mettez à jour le fichier .vsct dans le projet d’interface utilisateur utilisateur de l’application.  
  
-   Pour supprimer **Options** pages ou autres composants d’interpréteur de commandes de Visual Studio à partir de l’application, mettre à jour le fichier .pkgundef de l’application.  
  
-   Pour modifier d’autres aspects de l’apparence ou le comportement de l’interpréteur de commandes, mettre à jour le fichier .pkgdef de l’application.  
  
-   Certains aspects de l’interpréteur de commandes peuvent également être spécifiés lorsque l’application est démarrée. Pour ce faire, mettez à jour les paramètres dans l’appel au point d’entrée de démarrage de la appenvstub.dll.  
  
 Pour plus d’informations sur les différents éléments que vous pouvez personnaliser, consultez [éléments du Shell isolé](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Fonctionnalités standard de l’interpréteur de commandes isolé  
 Les fonctionnalités suivantes sont standard pour toutes les éditions de Visual Studio.  
  
|Catégorie de fonctionnalité|Fonctionnalité|  
|----------------------|-------------|  
|Fonctionnalités de l’IDE|Importer/exporter des paramètres<br /><br /> Programme d’installation du contrôle de boîte à outils<br /><br /> Liste des tâches et liste d’erreurs<br /><br /> Fenêtre Sortie<br /><br /> Page de démarrage<br /><br /> Propriétés (fenêtre)<br /><br /> Boîte à outils<br /><br /> Explorateur de solutions<br /><br /> Fenêtre Signet<br /><br /> Affichage de classes<br /><br /> Explorateur d'objets<br /><br /> Commande, fenêtre<br /><br /> Structure du document<br /><br /> Affichage des ressources<br /><br /> Outil externe<br /><br /> Windows Communication Foundation (WCF) ajouter une référence de Service<br /><br /> Language Integrated prise en charge de requête (LINQ)|  
|Concepteur/éditeur|Outils (recherche unifiée, définition de la source, l’héritage) de navigation du code<br /><br /> IntelliSense<br /><br /> Balises actives<br /><br /> Gestionnaire des extraits de code<br /><br /> Extraits de code<br /><br /> Refactorisation<br /><br /> Tabulation<br /><br /> Filtrage IntelliSense<br /><br /> Fenêtre Définition de code<br /><br /> Concepteur d'applications<br /><br /> Concepteur Windows Forms<br /><br /> Concepteur Windows Presentation Foundation (WPF)|  
|Débogage|Évaluateur d’Expression c#<br /><br /> Le débogage local<br /><br /> Le débogage managé<br /><br /> Modifier & Continuer<br /><br /> Débogage inter-threads<br /><br /> Visualisations<br /><br /> DataTips<br /><br /> Débogage natif<br /><br /> Débogage de script<br /><br /> Débogage d’interopérabilité<br /><br /> Débogage juste-à-temps (JIT)<br /><br /> Débogage multiprocessus<br /><br /> Débogage XSLT<br /><br /> Attacher au processus local<br /><br /> Points de trace<br /><br /> Contraintes de point d’arrêt|  
|Données|Explorateur de serveurs (simplifié - données uniquement)<br /><br /> Lier des données à des données locales (. MDF ou. MDB)<br /><br /> Lier les données à l’objet<br /><br /> Lier les données au service Web<br /><br /> Ensemble des contrôles de données<br /><br /> Éditeur XML<br /><br /> Lier des données à un serveur de base de données locale<br /><br /> Fenêtre Sources de données|  
|Web|Éditeur HTML<br /><br /> Navigateur web<br /><br /> Concepteur Web Forms<br /><br /> Projet de Site Web<br /><br /> Projet d’Application Web|  
|Extensibilité|Consomme des composants des VSPackages et MEF|  
  
## <a name="see-also"></a>Voir aussi  
 [Shell (isolé ou intégré)](../extensibility/shell-isolated-or-integrated.md)

