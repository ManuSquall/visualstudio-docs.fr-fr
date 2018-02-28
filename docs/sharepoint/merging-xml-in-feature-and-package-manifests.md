---
title: "Manifestes de fusionner du code XML dans les fonctionnalités et de packages | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 81e6f83dd4fc825e885843a47d45485918f7dabe
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>Fusionner du code XML dans des manifestes de fonctionnalités et de packages
  Fonctionnalités et les packages sont définis par [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichiers manifeste. Ces manifestes ajoutés au package sont une combinaison des données générées par les concepteurs et personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] les utilisateurs entrent dans le modèle de manifeste. Au moment de l’empaquetage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions avec fournie par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pour former le package [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichier manifeste. Les éléments semblables, avec les exceptions notées ultérieurement dans Exceptions de fusion, sont fusionnés pour éviter [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] erreurs de validation une fois que vous déployez les fichiers sur SharePoint, et pour rendre le manifeste des fichiers plus petits et plus efficace.  
  
## <a name="modifying-the-manifests"></a>Modification des manifestes  
 Vous ne peut pas modifier directement les fichiers manifestes du package jusqu'à ce que vous désactiviez les concepteurs de fonctionnalité ou un package. Toutefois, vous pouvez ajouter manuellement personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments pour le modèle de manifeste via les concepteurs de fonctionnalité et de package ou le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éditeur. Pour plus d’informations, consultez [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) et [Comment : personnaliser un Package de Solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Processus de fusion de manifeste de fonctionnalité et Package  
 Lors de la combinaison d’éléments personnalisés avec des éléments fournis par le concepteur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le processus suivant. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]vérifie si chaque élément a une valeur de clé unique. Si un élément n’a aucune valeur de clé unique, il est ajouté au fichier de manifeste du package. De même, les éléments qui ont plusieurs clés ne peuvent pas être fusionnés. Par conséquent, ils sont ajoutés au fichier manifeste.  
  
 Si un élément a une clé unique, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compare les valeurs du concepteur et de clés personnalisés. Si les valeurs correspondent, elles fusionnent en une seule valeur. Si les valeurs diffèrent, la valeur de clé de concepteur est ignorée et la valeur de clé personnalisée est utilisée. Collections sont également fusionnées. Par exemple, si l’objet généré par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] et personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] les deux contenir une collection d’assemblys, le manifeste du package contient uniquement une collection d’assemblys.  
  
## <a name="merge-exceptions"></a>Exceptions de fusion  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fusionne la plupart des concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments personnalisés semblables [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments tant qu’ils ont un attribut d’identification unique et unique. Toutefois, certains éléments n’ont pas l’identificateur unique requis pour [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] la fusion. Ces éléments sont appelés *exceptions de fusion*. Dans ce cas, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fusionne pas personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments fournis par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments, mais les ajoute au fichier de manifeste du package.  
  
 Voici une liste d’exceptions de fusion pour la fonctionnalité et de package [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichiers manifeste.  
  
|Designer|Élément XML|  
|--------------|-----------------|  
|Concepteur de fonctionnalités|ActivationDependency|  
|Concepteur de fonctionnalités|UpgradeAction|  
|Concepteur de packages|SafeControl|  
|Concepteur de packages|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Éléments de manifeste de fonctionnalité  
 Le tableau suivant est une liste de tous les éléments de manifeste de fonctionnalité qui peuvent être fusionnées et de leur clé unique qui est utilisée pour la correspondance.  
  
|Nom de l'élément|Clé unique|  
|------------------|----------------|  
|Fonctionnalité (tous les attributs)|*Nom d’attribut* (chaque nom d’attribut de l’élément de fonctionnalité est une clé unique.)|  
|ElementFile|Emplacement|  
|ElementManifests/ElementManifest|Emplacement|  
|Properties, propriété|Touche|  
|CustomUpgradeAction|Name|  
|CustomUpgradeActionParameter|Name|  
  
> [!NOTE]  
>  Étant le seul moyen de modifier l’élément CustomUpgradeAction personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éditeur, l’effet de fusion ne pas est faible.  
  
## <a name="package-manifest-elements"></a>Éléments de manifeste de package  
 Le tableau suivant est une liste de tous les éléments de manifeste de package qui peuvent être fusionnées et de leur clé unique qui est utilisée pour la correspondance.  
  
|Nom de l'élément|Clé unique|  
|------------------|----------------|  
|Solution (tous les attributs)|*Nom d’attribut* (chaque nom d’attribut de l’élément de Solution est une clé unique.)|  
|ApplicationResourceFiles/ApplicationResourceFile|Emplacement|  
|Assemblys / d’Assembly|Emplacement|  
|Série/ClassResources|Emplacement|  
|DwpFiles/DwpFile|Emplacement|  
|FeatureManifests/FeatureManifest|Emplacement|  
|Ressource|Emplacement|  
|RootFiles/RootFile|Emplacement|  
|SiteDefinitionManifests/SiteDefinitionManifest|Emplacement|  
|WebTempFile|Emplacement|  
|Modèlefichiers/TemplateFile|Emplacement|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Ajouter manuellement des fichiers déployés  
 Certains éléments de manifeste, tels que ApplicationResourceFile et DwpFiles, spécifient un emplacement qui inclut un nom de fichier. Toutefois, l’ajout d’une entrée de nom de fichier pour le modèle de manifeste n’ajoute pas du fichier sous-jacent au package. Vous devez ajouter le fichier au projet à inclure dans le package et définissez sa propriété Type de déploiement en conséquence.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de Solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  