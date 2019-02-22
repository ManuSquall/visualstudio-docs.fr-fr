---
title: Fusionner du code XML dans les fonctionnalités et de packages de manifestes | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8af9386d192c6dd96669dbfada298317cf5fe0e5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646302"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Fusion de contenu XML dans les manifestes de fonctionnalités et de packages
  Fonctionnalités et les packages sont définis par [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichiers manifeste. Ces manifestes ajoutés au package sont une combinaison de données générées par les concepteurs et personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] les utilisateurs entrent dans le modèle de manifeste. Au moment de l’empaquetage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions avec fourni par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pour former le package [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichier manifeste. Les éléments semblables, avec les exceptions notées plus loin dans les Exceptions de fusion, sont fusionnés pour éviter [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] erreurs de validation une fois que vous déployez les fichiers sur SharePoint, et pour rendre le manifeste de fichiers plus petits et plus efficace.

## <a name="modify-the-manifests"></a>Modifier les manifestes
 Vous ne peut pas modifier directement les fichiers manifestes du package jusqu'à ce que vous désactiviez les concepteurs de fonctionnalité ou un package. Toutefois, vous pouvez ajouter manuellement personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments pour le modèle de manifeste via les concepteurs de fonctionnalités et de packages ou [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éditeur. Pour plus d'informations, voir [Procédure : Personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) et [Comment : Personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Processus de fusion de manifeste de fonctionnalité et package
 Lors de la combinaison d’éléments personnalisés avec des éléments fournis par le concepteur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le processus suivant. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vérifie si chaque élément a une valeur de clé unique. Si un élément n’a aucune valeur de clé unique, elle est ajoutée au fichier de manifeste du package. De même, les éléments qui ont plusieurs clés ne peut pas être fusionnées. Par conséquent, ils sont ajoutés au fichier manifeste.

 Si un élément a une clé unique, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compare les valeurs du concepteur et les clés personnalisées. Si les valeurs correspondent, elles fusionnent en une seule valeur. Si les valeurs diffèrent, la valeur de clé de concepteur est ignorée et la valeur de clé personnalisée est utilisée. Les collections sont également fusionnées. Par exemple, si l’objet généré par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] et personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] les deux contiennent une collection d’assemblys, le manifeste ajouté au package ne contient qu’une seule collection d’assemblys.

## <a name="merge-exceptions"></a>Exceptions de fusion
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne la plupart des concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments avec personnalisée similaire [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments tant qu’ils ont un attribut d’identification unique, unique. Toutefois, certains éléments n’ont pas l’identificateur unique requis pour [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] la fusion. Ces éléments sont appelés *fusion exceptions*. Dans ce cas, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fusionne pas personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments et fourni par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments, mais les ajoute au fichier de manifeste du package.

 Voici une liste d’exceptions de fusion pour la fonctionnalité et de package [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichiers manifeste.

|Designer|Élément XML|
|--------------|-----------------|
|Concepteur de fonctionnalités|ActivationDependency|
|Concepteur de fonctionnalités|UpgradeAction|
|Concepteur de packages|SafeControl|
|Concepteur de packages|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Éléments de manifeste de fonctionnalité
 Le tableau suivant est une liste de tous les éléments de manifeste de fonctionnalité qui peuvent être fusionnées et de leur clé unique qui est utilisé pour la correspondance.

|Nom de l'élément|Clé unique|
|------------------|----------------|
|Fonctionnalité (tous les attributs)|*Nom d’attribut* (chaque nom d’attribut de l’élément de fonctionnalité est une clé unique.)|
|ElementFile|Emplacement|
|ElementManifests/ElementManifest|Emplacement|
|Properties, propriété|Touche|
|CustomUpgradeAction|Name|
|CustomUpgradeActionParameter|Name|

> [!NOTE]
>  Car la seule façon de modifier l’élément CustomUpgradeAction est personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éditeur, l’effet de fusion ne pas est faible.

## <a name="package-manifest-elements"></a>Éléments de manifeste de package
 Le tableau suivant est une liste de tous les éléments de manifeste de package qui peuvent être fusionnées et de leur clé unique qui est utilisé pour la correspondance.

|Nom de l'élément|Clé unique|
|------------------|----------------|
|Solution (tous les attributs)|*Nom d’attribut* (chaque nom d’attribut de l’élément de Solution est une clé unique.)|
|ApplicationResourceFiles/ApplicationResourceFile|Emplacement|
|Assemblys/Assembly|Emplacement|
|Série/ClassResources|Emplacement|
|DwpFiles/DwpFile|Emplacement|
|FeatureManifests/FeatureManifest|Emplacement|
|Ressources/ressources|Emplacement|
|RootFiles/RootFile|Emplacement|
|SiteDefinitionManifests/SiteDefinitionManifest|Emplacement|
|WebTempFile|Emplacement|
|TemplateFiles/TemplateFile|Emplacement|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Ajouter manuellement les fichiers déployés
 Certains éléments de manifeste, tels que ApplicationResourceFile et DwpFiles, spécifient un emplacement qui inclut un nom de fichier. Toutefois, l’ajout d’une entrée de nom de fichier pour le modèle de manifeste n’ajoute pas du fichier sous-jacent au package. Vous devez ajouter le fichier au projet à inclure dans le package et définissez sa propriété de Type de déploiement en conséquence.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
