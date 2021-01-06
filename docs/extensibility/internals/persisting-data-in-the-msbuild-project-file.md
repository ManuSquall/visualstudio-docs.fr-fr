---
title: Persistance des données dans le fichier projet MSBuild | Microsoft Docs
description: Découvrez comment rendre des données persistantes dans un fichier projet et utiliser IPersistXMLFragment pour conserver les données dans le fichier projet à travers les niveaux d’agrégation de sous-type de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20c6d79e6ea59b4993b4d6bfc5e165bdd952a3f9
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878077"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Données persistantes dans le fichier projet MSBuild
Un sous-type de projet peut avoir besoin de conserver des données spécifiques au sous-type dans le fichier projet pour une utilisation ultérieure. Un sous-type de projet utilise la persistance du fichier projet pour répondre aux exigences suivantes :

1. Conserver les données utilisées dans le cadre de la génération du projet. (Pour plus d’informations sur le Microsoft Build Engine, consultez [MSBuild](../../msbuild/msbuild.md).) Les informations relatives à la build peuvent être les suivantes :

    1. Données indépendantes de la configuration. Autrement dit, les données stockées dans des éléments MSBuild avec des conditions vides ou manquantes.

    2. Données dépendantes de la configuration. Autrement dit, les données stockées dans les éléments MSBuild qui sont conditionnés pour une configuration de projet particulière. Exemple :

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Conserver les données qui ne sont pas pertinentes pour la génération. Ces données peuvent être exprimées sous forme de code XML libre qui n’est pas validé par rapport à un schéma XML.

    1. Données indépendantes de la configuration.

    2. Données dépendantes de la configuration.

## <a name="persisting-build-related-information"></a>Persistance des informations de Build-Related
 La persistance des données utiles pour la génération d’un projet est gérée via MSBuild. Le système MSBuild gère une table principale d’informations relatives à la génération. Les sous-types de projet sont chargés d’accéder à ces données pour obtenir et définir des valeurs de propriété. Les sous-types de projet peuvent également augmenter la table de données liée à la génération en ajoutant des propriétés supplémentaires à rendre persistantes et en supprimant les propriétés afin qu’elles ne soient pas conservées.

 Pour modifier les données MSBuild, un sous-type de projet est responsable de la récupération de l’objet de propriété MSBuild à partir du système de projet de base via <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> est une interface implémentée sur le système de projet principal et les requêtes de sous-type de projet d’agrégation pour celle-ci en exécutant `QueryInterface` .

 La procédure suivante décrit les étapes de suppression d’une propriété à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Pour supprimer une propriété d’un fichier projet MSBuild

1. Appelez `QueryInterface` sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> le sous-type de projet.

2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> avec `pszPropName` défini sur la propriété que vous souhaitez supprimer.

### <a name="persisting-non-build-related-information"></a>Conservation des informations non liées à la génération
 La persistance des données dans les fichiers projet qui n’a pas d’importance pour la génération est gérée par le biais de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .

 Vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sur l' `project subtype aggregator` objet principal, l' `project subtype project configuration` objet ou les deux.

 Les points suivants décrivent les principaux concepts relatifs à la persistance des informations non liées à la génération.

- Le projet de base appelle sur le sous-type de projet principal (autrement dit, l’objet d’agrégation du sous-type de projet le plus à l’extérieur) pour charger et enregistrer des données indépendantes de la configuration, et il appelle sur les objets de configuration de projet de sous-type de projet pour charger ou enregistrer les données dépendantes de la configuration.

- Le projet de base appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> plusieurs fois pour chaque niveau d’agrégation de sous-type de projet et passe le GUID pour chaque niveau.

- Le projet de base transmet ou reçoit un fragment XML dédié à un sous-type de projet particulier et utilise ce mécanisme comme un moyen de conserver l’état entre les niveaux d’agrégation.

- Le projet de base appelle l’implémentation du sous-type de projet le plus à l’extérieur qui <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> transmet un GUID. Si le GUID appartient au sous-type de projet le plus à l’extérieur, il gère l’appel lui-même ; dans le cas contraire, il délègue l’appel à un sous-type de projet interne, et ainsi de suite, jusqu’à ce que le sous-type de projet auquel correspond le GUID soit trouvé.

- Un sous-type de projet peut également modifier le fragment XML avant ou après avoir délégué l’appel à un sous-type de projet interne. L’exemple suivant montre un extrait à partir d’un fichier projet, où le nom d’un fichier qui contient des propriétés spécifiques à un sous-type de projet est passé à ce sous-type de projet.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Voir aussi
- [Sous-types de projets](../../extensibility/internals/project-subtypes.md)
