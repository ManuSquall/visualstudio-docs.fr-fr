---
title: Vue d’ensemble des Options de configuration | Microsoft Docs
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
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4778fd01dde3f08bcc76cd6fc5dd5814f2bc913b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294292"
---
# <a name="configuration-options-overview"></a>Présentation des options de configuration
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans les projets [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] peut prendre en charge les configurations multiples qui peuvent être générées, débogué, exécution et/ou déployé. Une configuration est un type de build décrit avec un jeu nommé de propriétés, en général, les commutateurs du compilateur et les emplacements de fichiers. Par défaut, les nouvelles solutions contiennent deux configurations Debug et Release. Ces configurations peuvent être appliquées à l’aide de leurs paramètres par défaut ou modifiés pour répondre à vos besoins spécifiques de solution ou projet. Certains packages peuvent être générées de deux manières : en tant qu’ActiveX éditeur ou comme un composant sur place. Projets n’avez pas besoin de prendre en charge plusieurs configurations, toutefois. S’il n'existe qu’une seule configuration disponible, cette configuration est mappée dans toutes les configurations de solution.  
  
 Les configurations sont généralement consistant de deux parties : le nom de la configuration (par exemple, Debug ou Release) et les paramètres de plateforme. Nom de la plateforme d’une configuration identifie l’environnement que définir la configuration cible, par exemple une API ou une plateforme de système d’exploitation. Les utilisateurs de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Impossible de créer une plateforme ; ils doivent choisir dans les sélections à un projet VSPackage permet. Quand un utilisateur s’installe un VSPackage, la plateforme de livraison créée au cours du développement du package peut apparaître n’importe quel nom de la plateforme souhaitée selon les critères définis par le créateur du package. L’utilisateur peut ensuite sélectionner dans la liste des plateformes accessibles via le VSPackage lorsque les pages de propriétés sont instanciés.  
  
 Noms de plateforme sont facultatifs dans la mesure où pas tous les projets prennent en charge le concept de plateformes. Lorsqu’une configuration il manque un nom de plateforme, la chaîne « n/a » s’affiche dans l’interface utilisateur.  
  
 Chaque solution a son propre ensemble de configurations, qu’un seul d'entre eux peut être actif à la fois. Une configuration de solution est un ensemble de pas plus d’une configuration à partir de chaque projet. La stipulation « non supérieur à » est en raison de la possibilité d’exclure un projet à partir d’une configuration de solution. Les utilisateurs peuvent créer leurs propres configurations de solution personnalisée.  
  
 Le tableau suivant illustre le programme d’installation les configurations par défaut pour un projet. Les lignes sont étiquetées avec des noms de configuration et les colonnes avec des noms de plateforme.  
  
|Nom de la configuration|Plateforme : Win32|Plateforme : Win64|  
|------------------------|----------------------|----------------------|  
|Débogage|\<Paramètres de Win32 Debug >|\<Paramètres de Win64 Debug >|  
|Mise en production|\<Paramètres de Win32 de version >|\<Paramètres de Win64 de version >|  
|MyConfig|N/A|\<Paramètres de MyConfig Win64 >|  
  
> [!NOTE]
>  Impossible de créer une configuration de solution « MyConfig » qui exclut une plateforme « Win32 », sauf si le projet que vous ciblez ne prend pas en charge Win32.  
  
 Modification de la configuration active pour une solution sélectionne le jeu de configurations de projet qui sont créées, exécuter, déboguer ou déployé dans cette solution. Par exemple, si vous modifiez la configuration de solution active à partir de la version de débogage, tous les projets dans cette solution sont créées automatiquement avec la configuration du projet indiquée dans la configuration de solution débogage. Les configurations du projet sont généralement également nommée Debug, sauf si l’utilisateur a apporté des modifications manuelles dans le Gestionnaire de Configuration de l’environnement.  
  
 Les propriétés de configuration de solution stockées pour chaque projet incluent le nom du projet, nom de configuration de projet, les indicateurs pour indiquer s’il faut ou non pour générer ou déployer et nom de la plateforme. Pour plus d’informations, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
 L’utilisateur peut afficher et définir des paramètres de configuration de solution en sélectionnant la solution dans la hiérarchie (Explorateur de solutions) et en ouvrant les pages de propriétés. De même, vous pouvez afficher et définir les paramètres de configuration de projet en sélectionnant un projet dans l’Explorateur de solutions et en ouvrant les pages de propriétés pour ce projet.  
  
 L’utilisateur peut également générer un projet à l’aide de paramètres de configuration Release et tout le reste avec les paramètres de configuration Debug si nécessaire. Pour plus d’informations, consultez [Configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md).  
  
 Le diagramme suivant illustre la façon dont les interfaces qui prennent en charge les configurations de solution et de projet sont implémentées :  
  
 ![Graphique des Interfaces de configuration](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuration  
  
 Quelques remarques concernant le diagramme précédent :  
  
-   `IDispatch` est marqué comme étant facultatif dans l’objet de Configuration. Plus précisément, il est facultatif pour que les interfaces de configuration sur l’objet de recherche.  
  
-   `IVsDebuggableProjectCfg` est marqué comme facultatif dans l’objet de Configuration, mais est requis pour la prise en charge le débogage.  
  
-   `IVsProjectCfg2` est marqué comme facultatif dans l’objet de Configuration, mais est nécessaire pour la prise en charge de regroupement de sortie.  
  
-   Le `Config Provider` objet est marqué comme un objet facultatif, mais l’option est là pour l’implémenter. Vous pouvez implémenter l’objet sur l’objet de projet ou sur un objet distinct.  
  
-   `IVsCfgProvider2` est nécessaire pour la prise en charge de la plateforme et la modification de configuration. `IVsCfgProvider` est suffisant si vous n’implémentez pas cette fonctionnalité.  
  
-   Certains de ces objets indiqués dans le diagramme, comme des objets distincts peuvent être combinés dans la même classe si possible selon vos besoins de conception spécifiques. Dans d’autres rubriques de cette section, toutefois, les objets et les interfaces associées à ces objets seront abordées selon le scénario présenté dans le diagramme.  
  
-   Certains objets sont implémentées séparément. Par exemple, projet et solution génération se produisent sur des threads distincts et de l’objet pour gérer la vie build séparément à partir de l’objet qui décrit la configuration de la build.  
  
 Pour plus d’informations sur les interfaces de l’objet de Configuration et les interfaces de l’objet de fournisseur de Configuration dans le diagramme précédent, consultez [objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md). En outre, [Configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md) fournit des informations sur les interfaces de générateur de Configuration et de générer un objet de dépendance, et [Configuration de projet pour le déploiement de la gestion des](../../extensibility/internals/project-configuration-for-managing-deployment.md) Décrit les interfaces reliés au responsable du déploiement de la configuration et les objets de dépendance de déploiement. Enfin, [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md) décrit les interfaces du groupe de sorties et objet de sortie et l’utilisation des pages de propriétés pour afficher et définir les propriétés dépendantes de la configuration.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)

