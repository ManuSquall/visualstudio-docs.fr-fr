---
title: "Les données persistantes dans le fichier projet MSBuild | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b2bb73602a6cba07fe9cbde4ddae4219f5a2b350
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Données persistantes dans le fichier projet MSBuild
Un sous-type de projet devrez conserver les données spécifiques au sous-type dans le fichier projet pour une utilisation ultérieure. Un sous-type de projet utilise la persistance d’un fichier projet pour répondre aux exigences suivantes :  
  
1.  Conserver les données utilisées dans le cadre de la génération du projet. (Pour plus d’informations sur Microsoft Build Engine, consultez [MSBuild](../../msbuild/msbuild.md).) Informations relatives à la build peuvent :  
  
    1.  Données liées à la configuration. Autrement dit, les données stockées dans des éléments MSBuild avec des conditions vides ou manquantes.  
  
    2.  Données dépend de la configuration. Autrement dit, les données stockées dans des éléments MSBuild qui dépendent d’une configuration de projet particulier. Exemple :  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Conserver les données qui sont applique pas à générer. Ces données peuvent être exprimées en XML de forme libre qui n’est pas validée par rapport à un schéma XML.  
  
    1.  Données liées à la configuration.  
  
    2.  Données dépend de la configuration.  
  
## <a name="persisting-build-related-information"></a>Conserver les informations relatives à la Build  
 Persistance des données utiles pour la création d’un projet est gérée via MSBuild. Le système MSBuild tient à jour une table principale des informations relatives à la génération. Les sous-types de projet sont chargés pour accéder à ces données pour obtenir et définir des valeurs de propriété. Sous-types de projet peuvent augmenter également de la table de données relatives à la build en ajoutant des propriétés supplémentaires à rendre persistantes et en supprimant des propriétés afin qu’ils ne sont pas conservées.  
  
 Pour modifier les données de MSBuild, un sous-type de projet est chargé de récupérer l’objet de propriété MSBuild à partir du système de projet de base via <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>est une interface implémentée sur le système de projet principal et les requêtes de sous-type de projet agrégation pour qu’il en exécutant `QueryInterface`.  
  
 La procédure suivante présente les étapes de suppression d’une propriété à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Pour supprimer une propriété d’un fichier projet MSBuild  
  
1.  Appelez `QueryInterface` sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> du sous-type de projet.  
  
2.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> avec `pszPropName` défini sur la propriété que vous souhaitez supprimer.  
  
### <a name="persisting-non-build-related-information"></a>Build Non persistante les informations associées.  
 Persistance des données dans les fichiers projet qui n’a pas d’importance à générer est gérée via <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sur le principal `project subtype aggregator` objet, le `project subtype project configuration` objet, ou les deux.  
  
 Les points suivants décrivent les principaux concepts concernant la persistance de non-génération des informations connexes.  
  
-   Le projet de base appelle sur l’objet d’aggregator sous-type (autrement dit, le sous-type de projet extérieur) projet principal pour charger et enregistrer des données de configuration distinctes, et il appelle les objets de configuration de projet sous-type projet à charger ou enregistrer dépendantes de la configuration données.  
  
-   Le projet de base appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> plusieurs fois pour chaque niveau d’agrégation de sous-type de projet et passe le GUID pour chaque niveau.  
  
-   Le projet de base réussit ou reçoit un fragment XML qui est dédié à un sous-type de projet particulier et utilise ce mécanisme comme un moyen de rendre persistant l’état entre les niveaux d’agrégation.  
  
-   Le projet de base appelle le sous-type de projet extérieur <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implémentation en passant un GUID. Si le GUID appartient au sous-type de projet extérieur, il gère l’appel lui-même ; dans le cas contraire, elle délègue l’appel à un sous-type de projet interne et ainsi de suite jusqu'à trouve le sous-type de projet le GUID correspond à.  
  
-   Un sous-type de projet permettre également modifier le fragment XML avant ou après que elle délègue l’appel à un sous-type de projet interne. L’exemple suivant montre un extrait à partir d’un fichier de projet, où un nom d’un fichier qui contient les propriétés spécifiques à un sous-type de projet, est passé à ce sous-type de projet.  
  
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
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)