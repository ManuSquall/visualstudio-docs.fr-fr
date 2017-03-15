---
title: "Vue d’ensemble des Options de configuration | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 10
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2c188af385d75fed49f6e9aca6703365c3b63ca5
ms.lasthandoff: 02/22/2017

---
# <a name="configuration-options-overview"></a>Vue d’ensemble des Options de configuration
Dans les projets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut prendre en charge les configurations multiples qui peuvent être générées, déployée, exécution et/ou débogué. Une configuration est un type de build décrit avec un jeu nommé de propriétés, généralement des commutateurs de compilation et emplacements de fichiers. Par défaut, les nouvelles solutions contiennent deux configurations Debug et Release. Ces configurations peuvent être appliquées à l’aide de leurs paramètres par défaut ou modifiées pour répondre à vos besoins spécifiques de solution ou projet. Certains packages peuvent être générés de deux manières : en tant qu’un éditeur ActiveX ou un composant en place. Pour prendre en charge plusieurs configurations, toutefois, les projets est inutile. Si la seule configuration est disponible, cette configuration est mappée dans toutes les configurations de solution.  
  
 Configurations se composent généralement de deux parties : le nom de la configuration (par exemple Debug ou Release) et les paramètres de plateforme. Nom de la plateforme de configuration identifie l’environnement que définir la configuration cible, par exemple une API ou une plate-forme de système d’exploitation. Les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Impossible de créer une plateforme ; ils doivent choisir parmi les choix à un projet VSPackage permet. Lorsqu’une installation par l’utilisateur un VSPackage, la plate-forme de distribution créée pendant le développement du package peut apparaître n’importe quel nom de la plate-forme souhaitée selon les critères définis par le créateur du package. L’utilisateur peut ensuite sélectionner dans la liste des plates-formes disponibles via le VSPackage lorsque les pages de propriétés sont instanciés.  
  
 Noms de plateforme sont facultatifs pas tous les projets prenant en charge le concept de plateformes. Lorsqu’une configuration n’a pas un nom de la plateforme, la chaîne « n/a » s’affiche dans l’interface utilisateur.  
  
 Chaque solution possède son propre ensemble de configurations, un seul d'entre eux peut être active à la fois. Une configuration de solution est un ensemble de pas plus d’une configuration de chaque projet. La « pas plus de » stipulation est en raison de la possibilité d’exclure un projet à partir d’une configuration de solution. Les utilisateurs peuvent créer leurs propres configurations de solution personnalisée.  
  
 Le tableau suivant illustre la configuration de configurations par défaut pour un projet. Les lignes sont étiquetés avec les noms de configuration et les colonnes avec des noms de plateforme.  
  
|Nom de configuration|Plate-forme : Win32|Plate-forme : Win64|  
|------------------------|----------------------|----------------------|  
|Déboguer|\<Paramètres de Win32 Debug >|\<Déboguer les paramètres Win64 >|  
|Mise en production|\<Paramètres de Win32 version >|\<Paramètres de Win64 version >|  
|MyConfig|N/A|\<Paramètres de MyConfig Win64 >|  
  
> [!NOTE]
>  Impossible de créer une configuration de solution « MyConfig » qui exclut une plate-forme « Win32 », sauf si le projet que cible ne prend pas en charge Win32.  
  
 Modification de la configuration active pour une solution sélectionne l’ensemble des configurations de projet qui sont générés, exécuter, déboguer ou déployés dans cette solution. Par exemple, si vous modifiez la configuration de solution active à partir de la version de débogage, tous les projets dans cette solution sont générées automatiquement avec la configuration du projet indiquée dans la configuration de solution débogage. Les configurations du projet sont généralement également nommée Debug à moins que l’utilisateur a apporté des modifications manuelles dans le Gestionnaire de Configuration de l’environnement.  
  
 Les propriétés de configuration de solution stockées pour chaque projet incluent le nom du projet, nom de configuration de projet, indicateurs pour indiquer s’il faut ou non pour générer ou déployer et nom de la plateforme. Pour plus d’informations, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
 L’utilisateur peut afficher et définir des paramètres de configuration de solution en sélectionnant la solution dans la hiérarchie (Explorateur de solutions) et en ouvrant les pages de propriétés. De même, vous pouvez afficher et définir les paramètres de configuration de projet en sélectionnant un projet dans l’Explorateur de solutions et en ouvrant les pages de propriétés pour ce projet.  
  
 L’utilisateur peut également générer un projet avec les paramètres de configuration Release et les autres paramètres de configuration Debug si nécessaire. Pour plus d’informations, consultez [Configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md).  
  
 Le diagramme suivant montre comment les interfaces qui prennent en charge les configurations de projet et solution sont implémentées :  
  
 ![Graphique des Interfaces de configuration](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuration  
  
 Voici quelques remarques concernant le diagramme précédent :  
  
-   `IDispatch`est marqué comme facultatif dans l’objet de Configuration. Plus précisément, elle est facultative pour que les interfaces sur l’objet de configuration.  
  
-   `IVsDebuggableProjectCfg`est marqué comme facultatif dans l’objet de Configuration, mais est requis pour la prise en charge le débogage.  
  
-   `IVsProjectCfg2`est marqué comme facultatif dans l’objet de Configuration, mais est nécessaire pour la prise en charge de regroupement de sortie.  
  
-   Le `Config Provider` objet est marqué comme un objet facultatif, mais l’option est l’emplacement de l’implémenter. Vous pouvez implémenter l’objet sur l’objet de projet ou sur un objet distinct.  
  
-   `IVsCfgProvider2`est nécessaire pour la prise en charge de la plateforme et la modification de configuration. `IVsCfgProvider`est suffisant si vous n’implémentez pas cette fonctionnalité.  
  
-   Certains de ces objets dans le diagramme comme des objets distincts peuvent être combinés dans la même classe si possible en fonction de vos exigences de conception spécifiques. Dans d’autres rubriques de cette section, cependant, les objets et les interfaces associées à ces objets seront traitées selon le scénario présenté dans le diagramme.  
  
-   Certains objets sont implémentées séparément. Par exemple, projet et génération de la solution se produisent sur des threads séparés et de l’objet pour gérer la vie build séparément à partir de l’objet qui décrit la configuration de la build.  
  
 Pour plus d’informations sur les interfaces de l’objet de Configuration et les interfaces d’objet de fournisseur de Configuration dans le diagramme précédent, consultez [objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md). En outre, [Configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md) fournit des informations sur les interfaces de générateur de Configuration et créer un objet de dépendance, et [Configuration de projet pour le déploiement de la gestion des](../../extensibility/internals/project-configuration-for-managing-deployment.md) décrit les interfaces attachés aux configuration des objets dépendance responsable du déploiement et de déploiement. Enfin, [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md) décrit les interfaces du groupe de sorties et d’objet de sortie et l’utilisation des pages de propriétés pour afficher et définir les propriétés dépendantes de la configuration.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
