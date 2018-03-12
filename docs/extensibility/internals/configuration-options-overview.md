---
title: "Vue d’ensemble des Options de configuration | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edfe84e26a9331b8c40ec24b00387768bdbba82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-options-overview"></a>Vue d’ensemble des Options de configuration
Dans les projets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut prendre en charge les configurations multiples qui peuvent être générées, débogué, exécution et/ou déployé. Une configuration est un type de build avec un jeu nommé de propriétés, en général, les commutateurs du compilateur et les emplacements de fichiers. Par défaut, les nouvelles solutions contiennent deux configurations Debug et Release. Ces configurations peuvent être appliquées à l’aide de leurs paramètres par défaut ou modifiés pour répondre à vos besoins spécifiques de solution ou projet. Certains packages peuvent être générées de deux manières : en tant qu’un éditeur ActiveX ou un composant en place. Pour prendre en charge les configurations à plusieurs, toutefois, les projets est inutile. S’il n'existe qu’une seule configuration disponible, cette configuration est mappée dans toutes les configurations de solution.  
  
 Les configurations sont généralement consistant de deux parties : le nom de la configuration (par exemple, Debug ou Release) et les paramètres de plateforme. Nom de la plateforme de configuration identifie l’environnement que les cibles de configuration, par exemple une API définir ou la plateforme de système d’exploitation. Les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peut pas créer une plateforme ; il doit obligatoirement choisir à partir des sélections à un projet VSPackage permet. Lorsqu’un utilisateur s’installe un VSPackage, la plate-forme de distribution créée pendant le développement du package peut apparaître n’importe quel nom de la plateforme souhaitée selon les critères définis par le créateur du package. L’utilisateur peut ensuite sélectionner dans la liste des plateformes disponibles via le VSPackage lorsque les pages de propriétés sont instanciés.  
  
 Les noms de plateforme sont facultatifs pas tous les projets prenant en charge le concept de plateformes. Lorsqu’une configuration ne contient pas un nom de la plateforme, la chaîne « n/a » s’affiche dans l’interface utilisateur.  
  
 Chaque solution possède son propre ensemble de configurations, un seul d'entre eux peut être active à la fois. Une configuration de solution est un ensemble de pas plus d’une configuration à partir de chaque projet. La stipulation « pas plus de » est en raison de l’option pour exclure un projet à partir d’une configuration de solution. Les utilisateurs peuvent créer leurs propres configurations de solution personnalisée.  
  
 Le tableau suivant illustre le programme d’installation de configurations par défaut pour un projet. Les lignes sont étiquetés avec des noms de configuration et les colonnes avec des noms de plateforme.  
  
|Nom de la configuration|Plateforme, Win32|Plateforme : Win64|  
|------------------------|----------------------|----------------------|  
|Débogage|\<Déboguer des paramètres Win32 >|\<Déboguer les paramètres Win64 >|  
|Mise en production|\<Libérer les paramètres Win32 >|\<Libérer les paramètres Win64 >|  
|MyConfig|N/A|\<Les paramètres MyConfig Win64 >|  
  
> [!NOTE]
>  Impossible de créer une configuration de la solution « MyConfig » qui exclut une plateforme « Win32 », sauf si le projet que cible ne prend pas en charge Win32.  
  
 Modification de la configuration active pour une solution de sélectionne l’ensemble des configurations de projet qui sont créées, exécuter, déboguer ou déployé dans cette solution. Par exemple, si vous modifiez la configuration de solution active à partir de la version Debug, tous les projets dans cette solution sont créées automatiquement avec la configuration du projet indiquée dans la configuration Debug de la solution. Les configurations du projet sont généralement également nommé Debug, sauf si l’utilisateur a apporté des modifications manuelles dans le Gestionnaire de Configuration de l’environnement.  
  
 Les propriétés de configuration de solution stockées pour chaque projet incluent le nom du projet, nom de configuration de projet, les indicateurs pour indiquer s’il faut ou non générer ou déployer et nom de la plateforme. Pour plus d’informations, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
 L’utilisateur peut afficher et définir des paramètres de configuration de solution en sélectionnant la solution dans la hiérarchie (Explorateur de solutions), les pages de propriétés en ouvrant. De même, vous pouvez afficher et définir les paramètres de configuration de projet en sélectionnant un projet dans l’Explorateur de solutions et en ouvrant les pages de propriétés pour ce projet.  
  
 L’utilisateur peut également générer un projet à l’aide de paramètres de configuration Release et tout le reste avec les paramètres de configuration Debug si nécessaire. Pour plus d’informations, consultez [Configuration de projet pour la génération de](../../extensibility/internals/project-configuration-for-building.md).  
  
 Le diagramme suivant illustre l’implémentation des interfaces qui prennent en charge les configurations de projet et de solution :  
  
 ![Graphique des Interfaces de configuration](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuration  
  
 Quelques remarques concernant le diagramme précédent :  
  
-   `IDispatch`est marqué comme facultatif dans l’objet de Configuration. Plus précisément, elle est facultative pour que les interfaces de configuration sur l’objet.  
  
-   `IVsDebuggableProjectCfg`est marqué comme facultatif dans l’objet de Configuration, mais est requis pour la prise en charge le débogage.  
  
-   `IVsProjectCfg2`est marqué comme facultatif dans l’objet de Configuration, mais est nécessaire pour la prise en charge de regroupement de sortie.  
  
-   Le `Config Provider` objet est marqué en tant qu’objet facultatif, mais l’option est l’emplacement de l’implémenter. Vous pouvez implémenter l’objet sur l’objet de projet ou sur un objet distinct.  
  
-   `IVsCfgProvider2`est nécessaire pour la prise en charge de la plateforme et la modification de configuration. `IVsCfgProvider`est suffisant si vous n’implémentez pas cette fonctionnalité.  
  
-   Certains de ces objets indiqués dans le schéma comme des objets distincts peuvent être combinés dans la même classe, si possible en fonction de vos besoins de conception spécifiques. Dans d’autres rubriques de cette section, toutefois, les objets et les interfaces associées à ces objets seront abordées selon le scénario présenté dans le diagramme.  
  
-   Certains objets sont implémentées séparément. Par exemple, projet et génération de la solution se produisent sur des threads distincts et de l’objet pour gérer la vie build séparément à partir de l’objet qui décrit la configuration de la build.  
  
 Pour plus d’informations sur les interfaces de l’objet de Configuration et les interfaces de l’objet de fournisseur de Configuration dans le diagramme précédent, consultez [objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md). En outre, [Configuration de projet pour la génération de](../../extensibility/internals/project-configuration-for-building.md) fournit des informations sur les interfaces du Générateur de Configuration et de générer un objet de dépendance, et [Configuration de projet pour le déploiement de la gestion des](../../extensibility/internals/project-configuration-for-managing-deployment.md) Décrit les interfaces connectées au système de déploiement de configuration et les objets de dépendance de déploiement. Enfin, [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md) décrit les interfaces du groupe de sorties et de l’objet de sortie et l’utilisation des pages de propriétés pour afficher et définir les propriétés dépendantes de la configuration.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)