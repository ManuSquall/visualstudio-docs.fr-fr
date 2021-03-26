---
title: Vue d’ensemble des options de configuration | Microsoft Docs
description: En savoir plus sur les options pour les configurations de projet dans Visual Studio. Une configuration est un type de build décrit avec un jeu nommé de propriétés et d’emplacements de fichiers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad30e3f7b91e8a76715f66d9f6701597f3830bd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057128"
---
# <a name="configuration-options-overview"></a>Vue d’ensemble des options de configuration
Les projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peuvent prendre en charge plusieurs configurations qui peuvent être générées, déboguées, exécutées et/ou déployées. Une configuration est un type de build décrit avec un jeu nommé de propriétés, généralement les commutateurs de compilateur et les emplacements de fichiers. Par défaut, les nouvelles solutions contiennent deux configurations, *Debug* et *Release*. Ces configurations peuvent être appliquées à l’aide de leurs paramètres par défaut, ou modifiées pour répondre à vos besoins spécifiques en matière de solution et/ou de projet. Certains Packages peuvent être générés de deux manières : en tant qu’éditeur ActiveX ou en tant que composant sur place. Toutefois, les projets n’ont pas besoin de prendre en charge plusieurs configurations. Si une seule configuration est disponible, cette configuration est mappée dans toutes les configurations de solution.

 Les configurations se composent généralement de deux parties : le nom de la configuration (par exemple, *Debug* ou *Release*) et les paramètres de plateforme. Le nom de la plateforme d’une configuration identifie l’environnement ciblé par la configuration, par exemple un ensemble d’API ou une plate-forme de système d’exploitation. Les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peuvent pas créer de plateforme ; ils doivent choisir parmi les sélections qu’un VSPackage de projet autorise. Lorsqu’un utilisateur installe un VSPackage, la plateforme de remise créée pendant le développement du package peut surfacer n’importe quel nom de plateforme souhaité en fonction des critères définis par le créateur du package. L’utilisateur peut ensuite sélectionner dans la liste des plateformes rendues disponibles via le VSPackage quand les pages de propriétés sont instanciées.

 Les noms de plateformes sont facultatifs, car tous les projets ne prennent pas en charge le concept de plateformes. Lorsqu’une configuration ne dispose pas d’un nom de plateforme, la chaîne **N/a** s’affiche dans l’interface utilisateur.

 Chaque solution possède son propre ensemble de configurations, dont une seule peut être active à la fois. Une configuration de solution est un ensemble de plusieurs configurations de chaque projet. Le condition « pas plus de » est dû à l’option d’exclusion d’un projet d’une configuration de solution. Les utilisateurs peuvent créer leurs propres configurations de solution personnalisées.

 Le tableau suivant illustre la configuration des configurations typiques pour un projet. Les lignes sont étiquetées avec des noms de configuration et les colonnes avec des noms de plateforme.

|Nom de la configuration|Plateforme : Win32|Plateforme : Win64|
|------------------------|----------------------|----------------------|
|*Déboguer*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Version release*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|N/A|\<MyConfig Win64 settings>|

> [!NOTE]
> Vous ne pouvez pas créer une configuration de solution *MyConfig* qui exclut une plateforme Win32, sauf si le projet que vous ciblez ne prend pas en charge Win32.

 La modification de la configuration active d’une solution sélectionne l’ensemble des configurations de projet qui sont générées, exécutées, déboguées ou déployées dans cette solution. Par exemple, si vous modifiez la configuration de la solution active de *mise en version* à *Déboguer*, tous les projets de cette solution sont générés automatiquement avec la configuration des projets indiquée dans la configuration de débogage de la solution. Les configurations des projets sont également nommées *Debug* , sauf si l’utilisateur a apporté des modifications manuelles à l’Configuration Manager de l’environnement.

 Les propriétés de configuration de solution stockées pour chaque projet incluent le nom du projet, le nom de la configuration du projet, les indicateurs pour indiquer s’il faut ou non générer ou déployer, ainsi que le nom de la plateforme. Pour plus d’informations, consultez Configuration de la [solution](../../extensibility/internals/solution-configuration.md).

 L’utilisateur peut afficher et définir les paramètres de configuration de la solution en sélectionnant la solution dans la hiérarchie (Explorateur de solutions) et en ouvrant les pages de propriétés. De même, vous pouvez afficher et définir des paramètres de configuration de projet en sélectionnant un projet dans Explorateur de solutions et en ouvrant les pages de propriétés de ce projet.

 L’utilisateur peut également générer un projet à l’aide des paramètres de configuration Release et de tous les autres avec les paramètres de configuration de débogage, si nécessaire. Pour plus d’informations, consultez [configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md).

 Le diagramme suivant montre comment les interfaces qui prennent en charge les configurations de solution et de projet sont implémentées :

 ![Graphique des interfaces de configuration](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfaces de configuration

 Voici quelques remarques relatives au diagramme précédent :

- `IDispatch` est marqué comme étant facultatif dans l’objet de configuration. Plus précisément, il est facultatif d’avoir les interfaces de configuration sur l’objet Browse.

- `IVsDebuggableProjectCfg` est marqué comme étant facultatif dans l’objet de configuration, mais il est requis pour la prise en charge du débogage.

- `IVsProjectCfg2` est marquée comme étant facultative dans l’objet de configuration, mais est nécessaire pour la prise en charge du regroupement de sortie.

- L’objet fournisseur de configuration est marqué comme un objet facultatif, mais l’option est l’emplacement où l’implémenter. Vous pouvez implémenter l’objet sur l’objet de projet ou sur un objet distinct.

- `IVsCfgProvider2` est nécessaire pour la prise en charge de la plateforme et la modification de la configuration. `IVsCfgProvider` est suffisant si vous n’implémentez pas cette fonctionnalité.

- Certains de ces objets affichés dans le diagramme en tant qu’objets distincts peuvent être combinés dans la même classe si possible en fonction de vos exigences de conception spécifiques. Dans d’autres rubriques de cette section, toutefois, les objets et les interfaces associés à ces objets seront abordés en fonction du scénario présenté dans le diagramme.

- Certains objets sont implémentés séparément. Par exemple, la génération de projets et de solutions se produit sur des threads distincts et l’objet pour gérer la build vit séparément de l’objet décrivant la configuration de la Build.

  Pour plus d’informations sur les interfaces d’objet de configuration et les interfaces d’objet du fournisseur de configuration dans le diagramme précédent, consultez [objet de configuration de projet](../../extensibility/internals/project-configuration-object.md). En outre, la [configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md) fournit plus d’informations sur les interfaces d’objet de dépendance de génération et de configuration, et la [configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md) décrit les interfaces attachées aux objets de déploiement et de dépendance de déploiement de configuration. Enfin, la [configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md) décrit les interfaces de groupe de sortie et d’objet de sortie, ainsi que l’utilisation de pages de propriétés pour afficher et définir des propriétés dépendantes de la configuration.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
