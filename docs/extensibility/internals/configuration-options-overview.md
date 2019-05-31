---
title: Vue d’ensemble des Options de configuration | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b27df2b9b93276ade06f97c9e80fd0c0483ef963
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309996"
---
# <a name="configuration-options-overview"></a>Vue d’ensemble des options de configuration
Dans les projets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut prendre en charge les configurations multiples qui peuvent être générées, débogué, exécution et/ou déployé. Une configuration est un type de build décrit avec un jeu nommé de propriétés, en général, les commutateurs du compilateur et les emplacements de fichiers. Par défaut, les nouvelles solutions contiennent deux configurations, *déboguer* et *version*. Ces configurations peuvent être appliquées à l’aide de leurs paramètres par défaut ou modifiés pour répondre à vos besoins spécifiques de solution ou projet. Certains packages peuvent être générées de deux manières : en tant qu’ActiveX éditeur ou comme un composant sur place. Projets n’avez pas besoin de prendre en charge plusieurs configurations, toutefois. S’il n'existe qu’une seule configuration disponible, cette configuration est mappée dans toutes les configurations de solution.

 Les configurations sont généralement consistant de deux parties : le nom de configuration (tel que *déboguer* ou *version*) et les paramètres de plateforme. Nom de la plateforme d’une configuration identifie l’environnement que définir la configuration cible, par exemple une API ou une plateforme de système d’exploitation. Les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Impossible de créer une plateforme ; ils doivent choisir dans les sélections à un projet VSPackage permet. Quand un utilisateur s’installe un VSPackage, la plateforme de livraison créée au cours du développement du package peut apparaître n’importe quel nom de la plateforme souhaitée selon les critères définis par le créateur du package. L’utilisateur peut ensuite sélectionner dans la liste des plateformes accessibles via le VSPackage lorsque les pages de propriétés sont instanciés.

 Noms de plateforme sont facultatifs dans la mesure où pas tous les projets prennent en charge le concept de plateformes. Quand une configuration n’a pas un nom de plateforme, la chaîne **n/a** s’affiche dans l’interface utilisateur.

 Chaque solution a son propre ensemble de configurations, qu’un seul d'entre eux peut être actif à la fois. Une configuration de solution est un ensemble de pas plus d’une configuration à partir de chaque projet. La stipulation « non supérieur à » est en raison de la possibilité d’exclure un projet à partir d’une configuration de solution. Les utilisateurs peuvent créer leurs propres configurations de solution personnalisée.

 Le tableau suivant illustre le programme d’installation les configurations par défaut pour un projet. Les lignes sont étiquetées avec des noms de configuration et les colonnes avec des noms de plateforme.

|Nom de configuration|Plateforme : Win32|Plateforme : Win64|
|------------------------|----------------------|----------------------|
|*Déboguer*|\<Paramètres de Win32 Debug >|\<Paramètres de Win64 Debug >|
|*Version release*|\<Paramètres de Win32 de version >|\<Paramètres de Win64 de version >|
|*MyConfig*|N/A|\<Paramètres de MyConfig Win64 >|

> [!NOTE]
> Vous ne pouvez pas créer un *MyConfig* configuration de solution qui exclut une plateforme de Win32, sauf si le projet que vous ciblez ne prend pas en charge Win32.

 Modification de la configuration active pour une solution sélectionne le jeu de configurations de projet qui est créé, l’exécution, de débogage ou déployé dans cette solution. Par exemple, si vous modifiez la configuration de solution active *version* à *déboguer*, tous les projets au sein de cette solution sont automatiquement générés avec la configuration du projet indiquée dans le configuration de solution débogage. Les configurations du projet sont également appelées *déboguer* , sauf si l’utilisateur a apporté des modifications manuelles dans le Gestionnaire de Configuration de l’environnement.

 Les propriétés de configuration de solution stockées pour chaque projet incluent le nom du projet, nom de configuration de projet, les indicateurs pour indiquer s’il faut ou non pour générer ou déployer et nom de la plateforme. Pour plus d’informations, consultez [configuration de la Solution](../../extensibility/internals/solution-configuration.md).

 L’utilisateur peut afficher et définir des paramètres de configuration de solution en sélectionnant la solution dans la hiérarchie (Explorateur de solutions) et en ouvrant les pages de propriétés. De même, vous pouvez afficher et définir les paramètres de configuration de projet en sélectionnant un projet dans l’Explorateur de solutions et en ouvrant les pages de propriétés pour ce projet.

 L’utilisateur peut également générer un projet à l’aide des paramètres de configuration release et tout le reste avec les paramètres de configuration debug si nécessaire. Pour plus d’informations, consultez [configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md).

 Le diagramme suivant illustre la façon dont les interfaces qui prennent en charge les configurations de solution et de projet sont implémentées :

 ![Graphique des interfaces de configuration](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") interfaces de Configuration

 Quelques remarques concernant le diagramme précédent :

- `IDispatch` est marqué comme facultatif dans l’objet de configuration. Plus précisément, il est facultatif pour que les interfaces de configuration sur l’objet de recherche.

- `IVsDebuggableProjectCfg` est marqué comme facultatif dans l’objet de configuration, mais est requis pour la prise en charge le débogage.

- `IVsProjectCfg2` est marqué comme facultatif dans l’objet de configuration, mais est nécessaire pour la prise en charge de regroupement de sortie.

- L’objet de fournisseur de configuration est marqué comme un objet facultatif, mais l’option est là pour l’implémenter. Vous pouvez implémenter l’objet sur l’objet de projet ou sur un objet distinct.

- `IVsCfgProvider2` est nécessaire pour la prise en charge de la plateforme et la modification de configuration. `IVsCfgProvider` est suffisant si vous n’implémentez pas cette fonctionnalité.

- Certains de ces objets indiqués dans le diagramme, comme des objets distincts peuvent être combinés dans la même classe si possible selon vos besoins de conception spécifiques. Dans d’autres rubriques de cette section, toutefois, les objets et les interfaces associées à ces objets seront abordées selon le scénario présenté dans le diagramme.

- Certains objets sont implémentées séparément. Par exemple, projet et solution génération se produisent sur des threads distincts et de l’objet pour gérer la vie build séparément à partir de l’objet qui décrit la configuration de la build.

  Pour plus d’informations sur les interfaces d’objet de configuration et les interfaces d’objet de fournisseur de configuration dans le diagramme précédent, consultez [objet de configuration de projet](../../extensibility/internals/project-configuration-object.md). En outre, [configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md) fournit des informations sur la dépendance de build et de générateur de Configuration des interfaces d’objet et [configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md) Décrit les interfaces reliés au responsable du déploiement de la configuration et les objets de dépendance de déploiement. Enfin, [configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md) décrit le groupe de sorties et interfaces d’objet de sortie et l’utilisation des pages de propriétés pour afficher et définir les propriétés dépendantes de la configuration.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)