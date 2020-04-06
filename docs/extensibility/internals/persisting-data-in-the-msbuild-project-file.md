---
title: Données persistantes dans le fichier du projet MSBuild (fr) Microsoft Docs
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
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706699"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Données persistantes dans le fichier projet MSBuild
Un sous-type de projet peut avoir besoin de persister des données spécifiques au sous-type dans le fichier du projet pour une utilisation ultérieure. Un sous-type de projet utilise la persistance des dossiers de projet pour répondre aux exigences suivantes :

1. Données persistantes utilisées dans le cadre de la construction du projet. (Pour plus d’informations sur le moteur de construction Microsoft, voir [MSBuild](../../msbuild/msbuild.md).) Les informations relatives à la construction peuvent être :

    1. Données indépendantes de la configuration. C’est-à-dire les données stockées dans des éléments MSBuild avec des conditions vierges ou manquantes.

    2. Données dépendantes de la configuration. C’est-à-dire les données stockées dans des éléments MSBuild qui sont conditionnés pour une configuration particulière du projet. Par exemple :

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Des données persistantes qui ne sont pas pertinentes à construire. Ces données peuvent être exprimées en format libre XML qui n’est pas validée par rapport à un schéma XML.

    1. Données indépendantes de la configuration.

    2. Données dépendantes de la configuration.

## <a name="persisting-build-related-information"></a>Persistance de l’information liée à l’accumulation
 La persistance des données utiles à la construction d’un projet est gérée par MSBuild. Le système MSBuild tient une table maîtresse d’informations liées à la construction. Les sous-types de projet sont responsables de l’accès à ces données pour obtenir et définir la valeur des propriétés. Les sous-types de projet peuvent également augmenter le tableau de données lié à la construction en ajoutant des propriétés supplémentaires à persister et en supprimant les propriétés afin qu’elles ne soient pas persistées.

 Pour modifier les données MSBuild, un sous-type de projet est responsable de la récupération <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>de l’objet de propriété MSBuild à partir du système de projet de base à travers . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>est une interface mise en œuvre sur le système de projet de `QueryInterface`base et les requêtes de sous-type de projet d’agrégation pour elle en cours d’exécution .

 La procédure suivante décrit les étapes pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>enlever une propriété à l’aide de .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Supprimer une propriété d’un fichier de projet MSBuild

1. Faites `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> appel au sous-type du projet.

2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` avec l’ensemble de la propriété que vous voulez supprimer.

### <a name="persisting-non-build-related-information"></a>Persistance d’informations connexes non-build
 La persistance des données dans les fichiers de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>projet qui n’a pas d’importance à construire est traitée à travers .

 Vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implémenter sur l’objet principal, `project subtype aggregator` l’objet, `project subtype project configuration` ou les deux.

 Les points suivants décrivent les principaux concepts concernant la persistance de l’information non-construite.

- Le projet de base fait appel au sous-type principal du projet (c’est-à-dire le sous-type de projet le plus externe) objet d’agrégateur pour charger et enregistrer des données indépendantes de configuration, et il fait appel aux objets de configuration du projet de sous-type pour charger ou enregistrer les données dépendantes de configuration.

- Le projet de base <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> appelle les méthodes de plusieurs fois pour chaque niveau d’agrégation de sous-type de projet, et passe le GUID pour chaque niveau.

- Le projet de base passe ou reçoit un fragment XML qui est dédié à un sous-type de projet particulier et utilise ce mécanisme comme un moyen de maintenir l’état entre les niveaux d’agrégation.

- Le projet de base appelle la mise <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>en œuvre du sous-type de projet le plus externe en passant dans un GUID. Si le GUID appartient au sous-type de projet le plus externe, il gère l’appel lui-même; sinon il délégue l’appel à un sous-type de projet intérieur, et ainsi de suite, jusqu’à ce que le sous-type de projet que le GUID correspond à se trouve.

- Un sous-type de projet peut également modifier le fragment XML avant ou après qu’il délégue l’appel à un sous-type de projet intérieur. L’exemple suivant montre un extrait d’un fichier de projet, où le nom d’un fichier contenant des propriétés spécifiques à un sous-type de projet, est transmis à ce sous-type de projet.

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
