---
title: Conservation des données dans le fichier projet MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 362a4c09e3e0c732d939cf42b926b003260c4b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988120"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Données persistantes dans le fichier projet MSBuild
Un sous-type de projet peut devoir conserver les données de sous-type dans le fichier projet pour une utilisation ultérieure. Un sous-type de projet utilise la persistance d’un fichier projet pour répondre aux exigences suivantes :  
  
1.  Conserver les données utilisées dans le cadre de la génération du projet. (Pour plus d’informations sur Microsoft Build Engine, consultez [MSBuild](../../msbuild/msbuild.md).) Informations liées à la génération peuvent soit :  
  
    1.  Données de configuration indépendantes. Autrement dit, les données stockées dans des éléments MSBuild avec des conditions vides ou manquantes.  
  
    2.  Dépend de la configuration des données. Autrement dit, les données stockées dans des éléments MSBuild qui sont soumises pour une configuration de projet particulier. Exemple :  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Conserver les données qui sont applique pas à générer. Ces données peuvent être exprimées au format XML libre qui n’est pas validé par rapport à un schéma XML.  
  
    1.  Données de configuration indépendantes.  
  
    2.  Dépend de la configuration des données.  
  
## <a name="persisting-build-related-information"></a>Conserver les informations liées à la génération  
 Persistance des données utiles pour la création d’un projet est gérée via MSBuild. Le système MSBuild tient à jour une table principale des informations relatives à la build. Les sous-types de projet sont responsables de l’accès à ces données pour obtenir et définir des valeurs de propriété. Les sous-types de projet peuvent également d’étendre la table de données liées à la génération en ajoutant des propriétés supplémentaires à rendre persistantes et en supprimant les propriétés afin qu’ils ne sont pas conservées.  
  
 Pour modifier les données de MSBuild, un sous-type de projet est chargé de récupérer l’objet de propriété MSBuild à partir du système de projet de base via <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> est une interface implémentée sur le système de projet principal et les requêtes de sous-type de projet agrégation pour lui en exécutant `QueryInterface`.  
  
 La procédure suivante décrit les étapes de suppression d’un à l’aide de la propriété <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Pour supprimer une propriété d’un fichier projet MSBuild  
  
1.  Appelez `QueryInterface` sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> du sous-type de projet.  
  
2.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> avec `pszPropName` défini sur la propriété que vous souhaitez supprimer.  
  
### <a name="persisting-non-build-related-information"></a>Conserver les informations connexes Non-Build  
 Persistance des données dans les fichiers projet qui n’a pas d’importance à générer est gérée via <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sur les principaux `project subtype aggregator` objet, le `project subtype project configuration` objet, ou les deux.  
  
 Les points suivants décrivent les principaux concepts concernant la persistance des informations connexes non-build.  
  
-   Le projet de base appelle sur l’objet d’agrégation sous-type (autrement dit, le sous-type de projet extérieur) projet principal pour charger et enregistrer des données indépendantes de configuration, et il appelle sur les objets de configuration de projet de sous-type projet à charger ou enregistrer dépendantes de la configuration données.  
  
-   Le projet de base appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> plusieurs fois pour chaque niveau d’agrégation de sous-type de projet et passe le GUID pour chaque niveau.  
  
-   Le projet de base passe ou reçoit un fragment XML qui est dédié à un sous-type de projet particulier et utilise ce mécanisme de persistance de l’état entre les niveaux d’agrégation.  
  
-   Le projet de base appelle le sous-type de projet extérieur <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implémentation en passant un GUID. Si le GUID appartient au sous-type de projet extérieur, il gère l’appel lui-même ; Sinon, elle délègue l’appel à un sous-type de projet interne et ainsi de suite, jusqu'à ce que le sous-type de projet qui le GUID correspond à est trouvé.  
  
-   Un sous-type de projet peut également modifier le fragment XML avant ou après que elle délègue l’appel à un sous-type de projet interne. L’exemple suivant montre un extrait à partir d’un fichier de projet, où un nom d’un fichier qui contient les propriétés spécifiques à un sous-type de projet, est passée à ce sous-type de projet.  
  
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