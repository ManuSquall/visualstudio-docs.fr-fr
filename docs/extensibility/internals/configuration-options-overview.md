---
title: Aperçu des options de configuration (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709410"
---
# <a name="configuration-options-overview"></a>Aperçu des options de configuration
Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets en peuvent prendre en charge plusieurs configurations qui peuvent être construites, débogées, exécutées et/ou déployées. Une configuration est un type de build décrit avec un ensemble de propriétés nommés, généralement compiler les commutateurs et les emplacements de fichiers. Par défaut, les nouvelles solutions contiennent deux configurations, *Debug* et *Release*. Ces configurations peuvent être appliquées à l’aide de leurs paramètres par défaut, ou modifiées pour répondre à vos exigences spécifiques en matière de solution et/ou de projet. Certains paquets peuvent être construits de deux façons : en tant qu’éditeur ActiveX ou en tant que composant en place. Les projets n’ont toutefois pas besoin de prendre en charge plusieurs configurations. S’il n’y a qu’une seule configuration disponible, cette configuration est cartographiée dans toutes les configurations de solutions.

 Les configurations se composent généralement de deux parties : le nom de configuration (comme *Debug* ou *Release*) et les paramètres de la plate-forme. Le nom de la plate-forme d’une configuration identifie l’environnement que la configuration cible, comme un ensemble API ou une plate-forme de système d’exploitation. Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateurs de ne peuvent pas créer une plate-forme; ils doivent choisir parmi les sélections qu’un projet VSPackage permet. Lorsqu’un utilisateur installe un VSPackage, la plate-forme de livraison créée lors du développement du paquet peut faire surface n’importe quel nom de plate-forme souhaité en fonction des critères fixés par le créateur du paquet. L’utilisateur peut ensuite choisir parmi la liste des plates-formes mises à disposition via le VSPackage lorsque les pages de propriété sont instantanées.

 Les noms de plateformes sont facultatifs puisque tous les projets ne prennent pas en charge le concept de plates-formes. Lorsqu’une configuration n’a pas de nom de plate-forme, la chaîne **N/A** s’affiche dans l’interface utilisateur.

 Chaque solution a son propre ensemble de configurations, dont une seule peut être active à la fois. Une configuration de solution est un ensemble d’une configuration de pas plus d’une configuration de chaque projet. La stipulation "pas plus que" est due à l’option d’exclure un projet d’une configuration de solution. Les utilisateurs peuvent créer leurs propres configurations de solutions personnalisées.

 Le tableau suivant illustre la configuration typique des configurations d’un projet. Les lignes sont étiquetées avec des noms de configuration et les colonnes avec des noms de plate-forme.

|Nom de la configuration|Plateforme: Win32|Plateforme: Win64|
|------------------------|----------------------|----------------------|
|*Débogage*|\<Debug Win32 paramètres>|\<Debug Win64 paramètres>|
|*Libérer*|\<Communiqué Paramètres Win32>|\<Communiqué Paramètres Win64>|
|*MyConfig (en)*|N/A|\<Paramètres MyConfig Win64>|

> [!NOTE]
> Vous ne pouvez pas créer une configuration de solution *MyConfig* qui exclut une plate-forme Win32 à moins que le projet que vous ciblez ne prend pas en charge Win32.

 Changer la configuration active d’une solution sélectionne l’ensemble des configurations de projet qui sont construites, exécutées, débogées ou déployées dans cette solution. Par exemple, si vous modifiez la configuration de la solution active de *Release* à *Debug,* tous les projets de cette solution sont automatiquement intégrés avec la configuration des projets indiquée dans la configuration de déboise de la solution. Les configurations des projets sont également nommées *Debug* à moins que l’utilisateur n’ait apporté des modifications manuelles dans le gestionnaire de configuration de l’environnement.

 Les propriétés de configuration de solution stockées pour chaque projet comprennent le nom du projet, le nom de configuration du projet, les drapeaux pour indiquer s’il faut ou non construire ou déployer, et le nom de la plate-forme. Pour plus d’informations, voir [configuration Solution](../../extensibility/internals/solution-configuration.md).

 L’utilisateur peut afficher et définir les paramètres de configuration des solutions en sélectionnant la solution dans la hiérarchie (Solution Explorer) et en ouvrant les pages de propriété. De même, vous pouvez afficher et définir les paramètres de configuration du projet en sélectionnant un projet dans Solution Explorer et en ouvrant les pages de propriété pour ce projet.

 L’utilisateur peut également construire un projet en utilisant les paramètres de configuration de version et tout le reste avec des paramètres de configuration de débogé si nécessaire. Pour plus d’informations, voir [configuration du projet pour la construction](../../extensibility/internals/project-configuration-for-building.md).

 Le diagramme suivant montre comment les interfaces qui prennent en charge les configurations de solutions et de projet sont implémentées :

 ![Configuration interfaces graphique](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfaces de configuration

 Quelques notes relatives au diagramme précédent :

- `IDispatch`est marqué comme facultatif dans l’objet de configuration. Plus précisément, il est facultatif d’avoir les interfaces de configuration sur l’objet de navigation.

- `IVsDebuggableProjectCfg`est marqué en option dans l’objet de configuration, mais est nécessaire pour débogage support.

- `IVsProjectCfg2`est marqué en option dans l’objet de configuration, mais est nécessaire pour le support de groupement de sortie.

- L’objet Config Provider est marqué comme un objet facultatif, mais l’option est l’endroit où l’implémenter. Vous pouvez implémenter l’objet sur l’objet du projet ou sur un objet séparé.

- `IVsCfgProvider2`est nécessaire pour le support de la plate-forme et l’édition de configuration. `IVsCfgProvider`est suffisant si vous n’implémentez pas cette fonctionnalité.

- Certains de ces objets montrés dans le diagramme comme des objets séparés peuvent être combinés dans la même classe lorsque pratique en fonction de vos exigences de conception spécifiques. Dans d’autres sujets de cette section, cependant, les objets et les interfaces associées à ces objets seront discutés selon le scénario présenté dans le diagramme.

- Certains objets sont mis en œuvre séparément. Par exemple, le projet et la construction de solutions se produisent sur des fils séparés et l’objet pour gérer les vies de construction séparément de l’objet décrivant la configuration de la construction.

  Pour plus d’informations sur les interfaces d’objets de configuration et les interfaces d’objets du fournisseur de configuration dans le diagramme précédent, voir [l’objet de configuration du projet](../../extensibility/internals/project-configuration-object.md). En outre, [la configuration du projet pour](../../extensibility/internals/project-configuration-for-building.md) la construction fournit plus d’informations sur le constructeur de configuration et de construire des interfaces d’objets de dépendance, et la configuration du projet pour gérer le [déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md) décrit davantage les interfaces attachées au déployeur de configuration et les objets de dépendance de déploiement. Enfin, [la configuration du projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md) décrit les interfaces de groupe de sortie et d’objet de sortie, ainsi que l’utilisation de pages de propriété pour afficher et définir les propriétés dépendantes de la configuration.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configuration du projet pour la construction](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de solution](../../extensibility/internals/solution-configuration.md)
