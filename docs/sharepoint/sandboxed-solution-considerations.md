---
title: "Consid&#233;rations sur les solutions bac &#224; sable (sandbox)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "solutions de batterie (développement SharePoint dans Visual Studio)"
  - "solutions bac à sable (sandbox) (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, solutions de batterie"
  - "développement SharePoint dans Visual Studio, solutions bac à sable (sandbox)"
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Consid&#233;rations sur les solutions bac &#224; sable (sandbox)
  Les *solutions bac à sable \(sandbox\)* sont une nouveauté de Microsoft SharePoint 2010 qui permettent aux utilisateurs de collections de sites de télécharger leurs propres solutions de code  \(composants WebPart personnalisés, par exemple\).  
  
 Une application SharePoint dans une solution bac à sable est conçue pour s'exécuter dans un processus contrôlé sécurisé ayant accès à une zone limitée de la batterie de serveurs Web.  Microsoft SharePoint 2010 fait appel à différentes fonctionnalités, à des galeries de solutions, à un systèmes de surveillance et à une infrastructure de validation pour activer les solutions bac à sable \(sandbox\).  
  
## Spécification du niveau de confiance du projet  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prend en charge les solutions bac à sable \(sandbox\) via une propriété de projet booléenne appelée *Sandboxed Solution*.  Cette propriété peut être définie à tout moment ou spécifiée au moment de la création du projet dans l'**Assistant Personnalisation de SharePoint**.  
  
> [!NOTE]  
>  La modification de la propriété *Sandboxed Solution* d'un projet à l'issue de sa création risque de provoquer des erreurs de validation.  
  
 La solution est considérée comme une solution de batterie, si la propriété *Sandboxed Solution* a la valeur **false** ou si vous choisissez l'option **Déployer en tant que solution de batterie**.  Toutefois, la solution n'est pas traitée de la même manière qu'une solution de batterie, si la propriété *Sandboxed Solution* a la valeur **true** ou si vous sélectionnez l'option **Déployer en tant que solution bac à sable \(sandbox\)** dans l'Assistant.  
  
## Hiérarchie des sites SharePoint  
 Pour comprendre le mode de fonctionnement des solutions bac à sable \(sandbox\), il est important de savoir que les sites SharePoint sont organisés de façon hiérarchique.  L'élément supérieur correspond à la batterie de serveurs Web. Tous Les autres éléments lui sont subordonnés :  
  
 Batterie de serveurs Web  
  
 Application Web A  
  
 Collection de sites A1  
  
 Site A1a  
  
 Application Web B  
  
 Collection de sites B1  
  
 Site B1a  
  
 Site B1b  
  
 Collection de sites B2  
  
 Site B2a  
  
 Comme vous pouvez le voir, les batteries de serveurs Web peuvent contenir une ou plusieurs applications Web qui, à leur tour, peuvent regrouper une ou plusieurs collections de sites composées elles\-mêmes de sous\-sites, et ainsi de suite.  Les modifications apportées à une collection de sites concernent exclusivement cette collection de sites.  Toutefois, les changements effectués au niveau de la batterie de serveurs Web affectent toutes les collections de sites de la batterie.  
  
 Windows SharePoint Services 3.0 \(WSS\) est prévu pour déployer des solutions uniquement au niveau de la batterie, à la différence de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] qui assure le déploiement au niveau de la batterie \(solution de batterie\) ou de la collection de sites \(solution bac à sable \(sandbox\)\).  
  
## Intérêt des solutions bac à sable \(sandbox\)  
 Dans WSS 3.0, les solutions ne pouvaient être déployées qu'au niveau de la batterie.  Il était donc possible de déployer des solutions potentiellement dangereuses ou présentant des risques d'instabilité susceptibles de perturber le fonctionnement de la totalité de la batterie de serveurs Web et de l'ensemble des collections de sites et des applications sous\-jacentes.  Or, l'intérêt des solutions bac à sable est de limiter le déploiement de vos solutions à une sous\-zone de la batterie de services ou à une collection de sites spécifique.  Pour assurer une protection supplémentaire, l'assembly de la solution n'est pas chargé dans le processus [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] principal \(w3wp.exe\).  À la place, il est chargé dans un processus distinct \(SPUCWorkerProcess.exe\).  Ce processus est surveillé et met en œuvre des quotas et des limitations pour protéger la batterie contre les solutions bac à sable qui procèdent à des activités malveillantes, telles que l'exécution de boucles serrées qui consomment beaucoup de cycles microprocesseurs.  
  
## Galerie des solutions de collection de sites  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 dispose d'une fonction qui est appelée « galerie des solutions de collection de sites. » Vous pouvez accéder à cette fonctionnalité depuis la page Administration centrale de SharePoint 2010 ou en ouvrant le menu **Actions de site**, en choisissant **Paramètres du site**, puis en choisissant le lien **Solutions** sous  **Galeries** sur le site SharePoint.  Les galeries de solutions sont en quelque sorte des référentiels de solutions qui permettent aux administrateurs de collections de sites de gérer des solutions dans leurs collections de sites.  
  
 La galerie de solutions est une bibliothèque de documents stockée sur le site Web racine du site SharePoint.  Elle remplace les modèles de site et prend en charge les packages de solution.  Lorsqu'un fichier de package de solution SharePoint \(.wsp\) est téléchargé, il est traité comme une solution bac à sable \(sandbox\).  
  
## Limitations des solutions bac à sable \(sandbox\)  
 Lorsqu'une solution bac à sable \(sandbox\) est déployée, l'étendue des fonctionnalités SharePoint mises à sa disposition est limitée pour réduire les risques de vulnérabilité.  Voici quelques\-unes des limitations prévues :  
  
-   Les solutions bac à sable \(sandbox\) ont accès à un sous\-ensemble restreint d'éléments de solution déployables.  Les modèles de projet SharePoint potentiellement vulnérables, tels que les définitions de site et les flux de travail, ne sont pas disponibles.  
  
-   SharePoint exécute le code de la solution bac à sable \(sandbox\) dans un processus \(SPUCWorkerProcess.exe\) indépendant du processus de pool d'applications \(w3wp.exe\) [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] principal.  
  
-   Les dossiers mappés ne peuvent pas être ajoutés au projet.  
  
-   Les types de l'assembly [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] Microsoft.Office.Server ne peuvent pas être utilisés dans les solutions bac à sable \(sandbox\).  De plus, seuls les types de l'assembly [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Microsoft.SharePoint peuvent être utilisés dans les solutions bac à sable \(sandbox\).  
  
 Il est important de savoir que le fait de spécifier une solution SharePoint en tant que solution bac à sable \(sandbox\) n'a aucune incidence sur le serveur SharePoint. Cela change uniquement la façon dont le projet SharePoint est déployé sur SharePoint à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et détermine les assemblys auxquels il est lié.  Cela n'a aucun impact sur le fichier .wsp généré et le fichier .wsp ne comporte aucune donnée ayant un lien direct avec la propriété *Sandboxed Solution*.  
  
## Spécifications des solutions bac à sable \(sandbox\)  
 Les solutions bac à sable \(sandbox\) prennent en charge les spécifications suivantes :  
  
-   Types de contenu\/Champs  
  
-   Actions personnalisées  
  
-   Flux de travail déclaratifs  
  
-   Récepteurs d'événements  
  
-   Légendes des fonctionnalités  
  
-   Définitions de listes  
  
-   Instances de listes  
  
-   Module\/Fichiers  
  
-   Navigation  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Prise en charge de tous les composants WebPart dérivés de `System.Web.UI.WebControls.WebParts.WebPart`  
  
-   WebParts  
  
-   Éléments de fonctionnalité WebTemplate \(au lieu de Webtemp.xml\)  
  
-   Composants Visual WebPart  
  
 Les solutions bac à sable \(sandbox\) ne prennent pas en charge les spécifications suivantes :  
  
-   Pages d'application  
  
-   Groupe d'actions personnalisées  
  
-   Fonctionnalités relatives aux batteries  
  
-   Élément `HideCustomAction`  
  
-   Fonctionnalités relatives aux applications Web  
  
-   Flux de travail avec code  
  
## Voir aussi  
 [Différences entre les solutions bac à sable &#40;sandbox&#41; et les solutions de batterie](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  