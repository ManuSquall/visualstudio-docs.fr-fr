---
title: "Donn&#233;es persistantes dans le fichier projet MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers de projet, la persistance des données dans"
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Donn&#233;es persistantes dans le fichier projet MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un sous\-type de projet peut avoir à rendre persistantes les données spécifiques de sous\-type dans le fichier projet pour une utilisation ultérieure.  Un sous\-type de projet utilise la persistance de fichier projet pour répondre aux conditions suivantes :  
  
1.  Conserver des données utilisées dans le cadre de la génération du projet.  \(Pour plus d'informations sur Microsoft Build Engine, consultez [MSBuild](http://msdn.microsoft.com/fr-fr/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).\) les informations relatives peuvent procéder comme suit :  
  
    1.  données pas liées.  Autrement dit, données stockées dans des éléments MSBuild dans des conditions vides ou manquantes.  
  
    2.  Données dépendantes de la configuration.  Autrement dit, données stockées dans les éléments MSBuild qui sont conditionnés pour une configuration de projet donnée.  Par exemple :  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Rendez persistantes les données il n'est pas appropriée générer que.  Ces données peut être exprimée dans le format libre XML qui n'est pas validé par rapport à un schéma XML.  
  
    1.  données pas liées.  
  
    2.  Données dépendantes de la configuration.  
  
## Rendre les informations relatives  
 La persistance des données utiles pour générer un projet s'effectue via MSBuild.  Le système MSBuild contient une table principale des informations relatives.  Sous\-types de projet sont chargées d'accéder à ces données pour obtenir et définir des valeurs de propriété.  Sous\-types de projet peuvent également augmenter la table de données génération\-mise en relation en y ajoutant des propriétés supplémentaires à rendre persistantes et en supprimant des propriétés et ne sont pas rendus persistants.  
  
 Pour modifier les données MSBuild, un sous\-type de projet est chargée de récupérer l'objet de propriétés MSBuild du système de projet de base via <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> est une interface implémentée sur le principal système de projet et sous\-type regroupant de projet recherche est en exécutant `QueryInterface`.  
  
 La procédure suivante indique les étapes permettant de supprimer une propriété à l'aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### Pour supprimer une propriété d'un fichier projet MSBuild  
  
1.  Appelez `QueryInterface` sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> de sous\-type de projet.  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> d'appel avec `pszPropName` affectez à la propriété que vous souhaitez supprimer.  
  
### Rendre les informations connexes de Non\-Génération  
 La persistance des données dans les fichiers projet qui n'importe pas pour générer s'effectue via <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sur l'objet principal d' `project subtype aggregator` , l'objet d' `project subtype project configuration` , ou les deux.  
  
 Les points suivants décrivent les concepts principaux concernant la persistance des informations liées à la génération.  
  
-   Les appels de base de projet à l'objet principal d'agrégation de sous\-type de projet \(autrement dit, le sous\-type extérieur de projet\) pour charger et d'enregistrer les données indépendantes de configuration, et en fait appel à des objets de configuration de projet de sous\-type de projet pour charger ou enregistrer des données dépendantes de la configuration.  
  
-   Le projet de base appelle les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> plusieurs fois pour chaque niveau de regroupement de sous\-type de projet, puis passe GUID pour chaque niveau.  
  
-   Le projet de base passe ou accepte un fragment XML consacré à un sous\-type de projet particulier et utilise ce mécanisme afin de rendre persistant l'état entre les niveaux d'agrégation.  
  
-   Le projet de base appelle l'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>de sous\-type extérieur de projet en passant un GUID.  Si le GUID appartient au sous\-type extérieur de projet, il traite l'appel elle\-même ; sinon il délègue l'appel à un sous\-type interne de projet, et ainsi de suite, jusqu'à ce que le sous\-type de projet auquel GUID correspondant soit trouvé.  
  
-   un sous\-type de projet peut également modifier le fragment XML avant ou après qu'il délègue l'appel à un sous\-type interne de projet.  L'exemple suivant affiche un extrait d'un fichier projet, où un nom d'un fichier qui contient des propriétés spécifiques à un sous\-type de projet, est passé à ce sous\-type de projet.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## Voir aussi  
 [Sous\-types de projets](../../extensibility/internals/project-subtypes.md)