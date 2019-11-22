---
title: Shell isolé Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36491d9d590a45256e297654f71652ab5de5cd98
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299727"
---
# <a name="visual-studio-isolated-shell"></a>Shell isolé Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le shell isolé Visual Studio vous permet de créer des applications autonomes qui peuvent s’exécuter côte à côte avec d’autres versions de Visual Studio. Il est principalement utilisé pour héberger des outils spécialisés qui peuvent utiliser les services Visual Studio, mais également personnaliser l’apparence et la personnalisation. Les fonctionnalités de Visual Studio et les groupes de commandes de menu peuvent être facilement activés et désactivés. Les noms d’application, les icônes d’application et les écrans de démarrage sont entièrement personnalisables. Pour obtenir la liste des fonctionnalités personnalisables, consultez [Personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md).  
  
 Pour utiliser un projet Shell isolé, vous devez installer le kit de développement logiciel (SDK) Visual Studio. À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Pour créer une application Shell isolée, démarrez avec un projet isolé Visual Studio Shell. Ce projet contient tout ce dont vous avez besoin pour développer et tester votre propre application d’interpréteur de commandes isolé. Lorsque vous êtes prêt à écrire le programme d’installation qui déploie votre application, vous devez récupérer le package redistribuable Shell isolé à partir de [Microsoft Visual Studio Shell (isolé) package redistribuable](https://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
> Avant de pouvoir accéder au package redistribuable de l’interpréteur de commandes isolé, vous serez invité à fournir une brève enquête client.  Après avoir complété l’enquête, vous serez redirigé vers une page de connexion à Visual Studio avec des liens de téléchargement de packages redistribuables.  Vous trouverez les liens de téléchargement lors des visites suivantes sur le site Visual Studio Connect sous l’onglet  **&#124; programmes Visual Studio 2015 intégré et environnement isolé** .  
  
> [!NOTE]
> Pour plus d’informations sur le déploiement d’une application basée sur un interpréteur de commandes isolé, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Utilisation de l’interpréteur de commandes isolé  
 Une application Shell isolée Visual Studio dispose d’un accès complet aux services Visual Studio et prend en charge la personnalisation et la personnalisation spéciales. Il existe plusieurs façons de personnaliser une application Shell isolée :  
  
- Vous pouvez utiliser les composants VSPackages et Managed Extensibility Framework (MEF) pour étendre une application Shell isolée comme vous le feriez dans n’importe quelle autre extension Visual Studio. Pour plus d’informations, consultez [extension de l’interpréteur de commandes isolé](../extensibility/extending-the-isolated-shell.md).  
  
- Pour rendre les fonctionnalités Visual Studio et les groupes de commandes de menu disponibles ou non, mettez à jour le fichier. vsct dans le projet d’interface utilisateur de l’application.  
  
- Pour supprimer des pages d' **options** ou d’autres composants de l’interpréteur de commandes Visual Studio de l’application, mettez à jour le fichier. pkgundef de l’application.  
  
- Pour modifier d’autres aspects de l’apparence ou du comportement de l’interpréteur de commandes, mettez à jour le fichier. pkgdef de l’application.  
  
- Certains aspects de l’interpréteur de commandes peuvent également être spécifiés au démarrage de l’application. Pour ce faire, mettez à jour les paramètres dans l’appel au point d’entrée de début de appenvstub. dll.  
  
  Pour plus d’informations sur les différents éléments que vous pouvez personnaliser, consultez [éléments de l’interpréteur de commandes isolé](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Fonctionnalités standard de l’interpréteur de commandes isolé  
 Les fonctionnalités suivantes sont standard pour toutes les éditions de Visual Studio.  
  
|Catégorie de fonctionnalité|Fonction|  
|----------------------|-------------|  
|Fonctionnalités de l’IDE|Paramètres d’importation/exportation<br /><br /> Programme d’installation du contrôle de boîte à outils<br /><br /> Liste des tâches & Liste d’erreurs<br /><br /> Sortie (fenêtre)<br /><br /> Page de démarrage<br /><br /> Fenêtre Propriétés<br /><br /> Boîte à outils<br /><br /> l’Explorateur de solutions<br /><br /> Fenêtre Signet<br /><br /> Affichage de classes<br /><br /> Explorateur d'objets<br /><br /> Commande, fenêtre<br /><br /> Structure du document<br /><br /> Affichage des ressources<br /><br /> Outil externe<br /><br /> Ajouter une référence de service Windows Communication Foundation (WCF)<br /><br /> Prise en charge de LINQ (Language Integrated Query)|  
|Éditeur/concepteur|Outils de navigation du code (recherche unifiée, définition de la source, héritage)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Gestionnaire des extraits de code<br /><br /> Extraits de code<br /><br /> Refactoring<br /><br /> Listing convivial<br /><br /> Filtrage IntelliSense<br /><br /> Fenêtre Définition de code<br /><br /> Concepteur d'applications<br /><br /> Concepteur Windows Forms<br /><br /> Concepteur Windows Presentation Foundation (WPF)|  
|Débogage|C#Évaluateur d’expression<br /><br /> Débogage local<br /><br /> Débogage managé<br /><br /> Modifier & Continuer<br /><br /> Débogage inter-threads<br /><br /> Visualisations<br /><br /> DataTips<br /><br /> Débogage natif<br /><br /> Débogage de script<br /><br /> Débogage d’interopérabilité<br /><br /> Débogage juste-à-temps (JIT)<br /><br /> Débogage multiprocessus<br /><br /> Débogage XSLT<br /><br /> Attacher au processus local<br /><br /> Points de trace<br /><br /> Contraintes de point d’arrêt|  
|Données|Explorateur de serveurs (simplifié-données uniquement)<br /><br /> Liaison de données aux données locales (. MDF ou. MDB<br /><br /> Liaison de données à un objet<br /><br /> Liaison de données au service Web<br /><br /> Ensemble complet de contrôles de données<br /><br /> Éditeur XML<br /><br /> Liaison de données au serveur de base de données local<br /><br /> Fenêtre Sources de données|  
|Web|Éditeur HTML<br /><br /> Navigateur web<br /><br /> Concepteur Web Forms<br /><br /> Projet de site Web<br /><br /> Projet d’application Web|  
|Extensibilité|Utilise les VSPackages et les composants MEF|  
  
## <a name="see-also"></a>Voir aussi  
 [Shell (isolé ou intégré)](../extensibility/shell-isolated-or-integrated.md)
