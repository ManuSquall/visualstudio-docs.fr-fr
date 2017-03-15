---
title: "Isolé du Shell Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 35
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: d6925bbb3fa432c098f62d223b1c1a7478ecca23
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-isolated-shell"></a>Isolé du Shell Visual Studio
Le shell Visual Studio isolé permet de créer des applications autonomes qui peuvent s’exécuter côte à côte avec d’autres versions de Visual Studio. Il est principalement utilisée pour héberger des outils spécialisés qui peuvent utiliser les services de Visual Studio, mais également avoir une apparence personnalisée et de personnalisation. Fonctionnalités Visual Studio et les groupes de commandes de menu peuvent être facilement activées et désactivées. Titres d’application, les icônes d’application et les écrans de démarrage sont entièrement personnalisables. Pour obtenir la liste des fonctionnalités personnalisables, consultez [personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md).  
  
 Pour travailler avec un projet de shell isolé, vous devez installer le Kit de développement Visual Studio. À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Pour créer une application de shell isolé, commencez avec un projet Visual Studio Shell isolé. Ce projet contient tout ce dont vous avez besoin pour développer et tester votre propre application shell isolé. Lorsque vous êtes prêt à écrire le programme d’installation qui permet de déployer votre application, vous devez obtenir le package redistribuable du shell isolé de [Package redistribuable Microsoft Visual Studio Shell (isolé)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Avant de pouvoir accéder le package redistribuable du shell isolé, vous devez remplir un questionnaire client brève.  Après avoir complété l’enquête, vous allez être redirigé vers une page de Visual Studio se connecter avec des liens de téléchargement de package redistribuable.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio se connecter sous le **programmes | VISUAL STUDIO 2015 intégré et SHELL isolé** onglet.  
  
> [!NOTE]
>  Pour plus d’informations sur la façon de déployer une application shell isolée, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Avec le shell isolé  
 Une application du shell Visual Studio isolé a un accès complet aux services de Visual Studio et prend en charge la personnalisation spécial et la personnalisation. Il existe plusieurs façons de personnaliser une application shell isolé :  
  
-   Vous pouvez utiliser des composants VSPackages et Managed Extensibility Framework (MEF) pour étendre une application de shell isolé comme vous souhaitez les utiliser dans n’importe quelle autre extension Visual Studio. Pour plus d’informations, consultez [extension de l’interpréteur de commandes isolé](../extensibility/extending-the-isolated-shell.md).  
  
-   Pour rendre les fonctionnalités de Visual Studio et les groupes de commandes de menu disponibles ou indisponibles, mettre à jour le fichier .vsct dans le projet d’interface graphique utilisateur de l’application.  
  
-   Pour supprimer **Options** pages ou autres composants d’interpréteur de commandes de Visual Studio à partir de l’application, mettre à jour le fichier .pkgundef de l’application.  
  
-   Pour modifier d’autres aspects de l’apparence ou le comportement de l’interpréteur de commandes, mettre à jour le fichier .pkgdef de l’application.  
  
-   Certains aspects de l’interpréteur de commandes peuvent également être spécifiés lorsque l’application est démarrée. Pour ce faire, mettez à jour les paramètres dans l’appel vers le point d’entrée de démarrage de la appenvstub.dll.  
  
 Pour plus d’informations sur les différents éléments que vous pouvez personnaliser, consultez [éléments du Shell isolé](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Fonctionnalités standard de l’interpréteur de commandes isolé  
 Les fonctionnalités suivantes sont standard pour toutes les éditions de Visual Studio.  
  
|Catégorie de fonctionnalité|Fonctionnalité|  
|----------------------|-------------|  
|Fonctionnalités de l’IDE|Importer/exporter des paramètres<br /><br /> Programme d’installation du contrôle de boîte à outils<br /><br /> Liste des tâches < liste d’erreurs<br /><br /> Fenêtre Sortie<br /><br /> Page de démarrage<br /><br /> Fenêtre Propriétés<br /><br /> Boîte à outils<br /><br /> Explorateur de solutions<br /><br /> Fenêtre Signet<br /><br /> Affichage de classes<br /><br /> Explorateur d'objets<br /><br /> Fenêtre Commande<br /><br /> Structure du document<br /><br /> Affichage des ressources<br /><br /> Outil externe<br /><br /> Windows Communication Foundation (WCF) ajouter une référence de Service<br /><br /> Langage intégré la prise en charge de requête (LINQ)|  
|Éditeur/concepteur|Code de navigation outils (recherche unifiée, définition de la source, l’héritage)<br /><br /> IntelliSense<br /><br /> Balises actives<br /><br /> Gestionnaire des extraits de code<br /><br /> Extraits de code<br /><br /> Refactorisation<br /><br /> Tabulation<br /><br /> Filtrage IntelliSense<br /><br /> Fenêtre Définition de code<br /><br /> Concepteur d'applications<br /><br /> Concepteur Windows Forms<br /><br /> Concepteur Windows Presentation Foundation (WPF)|  
|Débogage|Évaluateur d’Expression c#<br /><br /> Débogage local<br /><br /> Débogage managé<br /><br /> Modifier & Continuer<br /><br /> Débogage inter-threads<br /><br /> Visualisations<br /><br /> DataTips<br /><br /> Débogage en natif<br /><br /> Débogage de script<br /><br /> Débogage d’interopérabilité<br /><br /> Le débogage juste-à-temps (JIT)<br /><br /> Débogage de plusieurs processus<br /><br /> Débogage XSLT<br /><br /> Attacher à des processus locaux<br /><br /> Points de trace<br /><br /> Contraintes de point d’arrêt|  
|Données|Explorateur de serveurs (simplifié - données uniquement)<br /><br /> Lier des données aux données locales (. MDF ou. MDB)<br /><br /> Liaison de données à l’objet<br /><br /> Liaison de données au service Web<br /><br /> Ensemble des contrôles de données<br /><br /> Éditeur XML<br /><br /> Lier des données au serveur de base de données locale<br /><br /> Fenêtre Sources de données|  
|Web|Éditeur HTML<br /><br /> Navigateur web<br /><br /> Concepteur Web Forms<br /><br /> Projet de Site Web<br /><br /> Projet d'application web|  
|Extensibilité|Utilise des composants VSPackages et MEF|  
  
## <a name="see-also"></a>Voir aussi  
 [Shell (isolé ou intégré)](../extensibility/shell-isolated-or-integrated.md)
