---
title: Fusion de données XML dans des manifestes de fonctionnalités et de packages | Microsoft Docs
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
ms.openlocfilehash: 1378cddbc9770af923a98f1b7083a8792874b5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839725"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Fusionner des données XML dans des manifestes de fonctionnalités et de packages
  Les fonctionnalités et les packages sont définis par des [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichiers manifestes. Ces manifestes empaquetés sont une combinaison de données générées par les concepteurs et personnalisées [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] entrées dans le modèle de manifeste par les utilisateurs. Au moment de l’empaquetage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne les instructions personnalisées [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] avec le concepteur fourni [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pour former le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichier manifeste empaqueté. Les éléments similaires, avec les exceptions notées plus loin dans les exceptions de fusion, sont fusionnés pour éviter les [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Erreurs de validation après le déploiement des fichiers sur SharePoint, et pour rendre les fichiers manifeste plus petits et plus efficaces.

## <a name="modify-the-manifests"></a>Modifier les manifestes
 Vous ne pouvez pas modifier directement les fichiers manifestes empaquetés tant que vous n’avez pas désactivé la fonctionnalité ou les concepteurs de package. Toutefois, vous pouvez ajouter manuellement des [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments personnalisés au modèle de manifeste par le biais des concepteurs de fonctionnalités et de packages ou de l' [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éditeur. Pour plus d’informations, consultez [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) et [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Processus de fusion des manifestes de fonctionnalités et de packages
 Lors de la combinaison d’éléments personnalisés et d’éléments fournis par le concepteur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le processus suivant. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vérifie si chaque élément a une valeur de clé unique. Si un élément n’a pas de valeur de clé unique, il est ajouté au fichier manifeste empaqueté. De même, les éléments qui ont plusieurs clés ne peuvent pas être fusionnés. Par conséquent, elles sont ajoutées au fichier manifeste.

 Si un élément a une clé unique, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compare les valeurs du concepteur et des clés personnalisées. Si les valeurs correspondent, elles fusionnent en une seule valeur. Si les valeurs diffèrent, la valeur de clé du concepteur est ignorée et la valeur de clé personnalisée est utilisée. Les collections sont également fusionnées. Par exemple, si le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] et le personnalisé [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] contiennent tous les deux une collection d’assemblys, le manifeste empaqueté contient une seule collection d’assemblys.

## <a name="merge-exceptions"></a>Fusionner les exceptions
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne la plupart des [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments de concepteur avec des éléments personnalisés similaires, à [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] condition qu’ils aient un seul attribut d’identification unique. Toutefois, certains éléments n’ont pas l’identificateur unique requis pour la [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fusion. Ces éléments sont appelés *exceptions de fusion*. Dans ce cas, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fusionne pas les [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éléments personnalisés avec les éléments fournis par le concepteur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , mais les ajoute au fichier manifeste empaqueté.

 Voici une liste d’exceptions de fusion pour les fichiers manifeste de fonctionnalité et de package [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

|Designer|Élément XML|
|--------------|-----------------|
|Concepteur de fonctionnalités|ActivationDependency|
|Concepteur de fonctionnalités|UpgradeAction|
|Concepteur de packages|SafeControl|
|Concepteur de packages|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Éléments du manifeste de fonctionnalité
 Le tableau suivant répertorie tous les éléments de manifeste de fonctionnalité qui peuvent être fusionnés et leur clé unique utilisée pour la correspondance.

|Nom de l’élément|Clé unique|
|------------------|----------------|
|Fonctionnalité (tous les attributs)|*Nom* de l’attribut (chaque nom d’attribut de l’élément de fonctionnalité est une clé unique.)|
|ElementFile|Emplacement|
|ElementManifests/ElementManifest|Emplacement|
|Propriétés/propriété|Clé|
|CustomUpgradeAction|Nom|
|CustomUpgradeActionParameter|Nom|

> [!NOTE]
> Étant donné que la seule façon de modifier l’élément CustomUpgradeAction est dans l' [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] éditeur personnalisé, l’effet de la non fusion est faible.

## <a name="package-manifest-elements"></a>Éléments du manifeste du package
 Le tableau suivant répertorie tous les éléments de manifeste de package qui peuvent être fusionnés et leur clé unique utilisée pour la correspondance.

|Nom de l’élément|Clé unique|
|------------------|----------------|
|Solution (tous les attributs)|*Nom* de l’attribut (chaque nom d’attribut de l’élément de solution est une clé unique.)|
|ApplicationResourceFiles/ApplicationResourceFile|Emplacement|
|Assemblys/assembly|Emplacement|
|ClassResources/ClassResource|Emplacement|
|DwpFiles/DwpFile|Emplacement|
|FeatureManifests/FeatureManifest|Emplacement|
|Ressources/ressource|Emplacement|
|RootFiles/RootFile|Emplacement|
|SiteDefinitionManifests/SiteDefinitionManifest|Emplacement|
|WebTempFile|Emplacement|
|TemplateFiles/TemplateFile|Emplacement|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Ajouter manuellement des fichiers déployés
 Certains éléments de manifeste, tels que ApplicationResourceFile et DwpFiles, spécifient un emplacement qui comprend un nom de fichier. Toutefois, l’ajout d’une entrée de nom de fichier au modèle de manifeste n’ajoute pas le fichier sous-jacent au package. Vous devez ajouter le fichier au projet pour l’inclure dans le package et définir sa propriété type de déploiement en conséquence.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
