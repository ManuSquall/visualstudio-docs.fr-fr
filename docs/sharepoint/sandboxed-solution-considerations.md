---
title: "Considérations relatives à la Solution bac à sable | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0b510097dc21c385f67a9358eaca3997cbdc2316
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *Solutions bac à sable* sont une fonctionnalité de Microsoft SharePoint 2010 qui permet aux utilisateurs de collection de sites de télécharger leurs propres solutions de code personnalisé. Une solution bac à sable commune est aux utilisateurs de télécharger leurs propres composants WebPart.  
  
 Une application SharePoint sandboxed s’exécute dans un processus sécurisé et surveillé qui a accès à une partie limitée de la batterie de serveurs Web. Microsoft SharePoint 2010 utilise une combinaison de fonctionnalités, des galeries de solutions, des solutions d’analyse et une infrastructure de validation pour activer les solutions bac à sable.  
  
## <a name="specifying-project-trust-level"></a>Spécification du niveau de confiance de projet  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]prend en charge les solutions bac à sable via une propriété de projet booléenne appelées *Solution bac à sable*. Cette propriété peut être définie à tout moment dans le projet, ou il peut être spécifié lorsque vous créez le projet dans le **Assistant Personnalisation de SharePoint**.  
  
> [!NOTE]  
>  Modification de la *Solution bac à sable* propriété d’un projet après sa création peut provoquer des erreurs de validation.  
  
 La solution est considérée comme une solution de batterie si le *Solution bac à sable* est définie sur **false** ou si vous choisissez la **déployer une solution de batterie de serveurs** option. Toutefois, la solution est traitée différemment d’une solution de batterie de serveurs si la *Solution bac à sable* est définie sur **true** ou si vous choisissez la **déployer comme une solution bac à sable** option de l’Assistant.  
  
## <a name="sharepoint-site-hierarchy"></a>Hiérarchie de Site SharePoint  
 Pour comprendre les solutions bac à sable comment le travail, il est utile de savoir que les sites SharePoint sont hiérarchiques dans la portée. L’élément supérieur est appelé à la batterie de serveurs Web et autres éléments lui sont subordonnés :  
  
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
  
 Comme vous pouvez le voir, les batteries de serveurs Web peuvent contenir une ou plusieurs applications Web, qui à son tour peuvent contenir une ou plusieurs collections de sites, ce qui peuvent avoir des sous-sites et ainsi de suite. Modifications apportées à une collection de sites concernent uniquement que collection de sites et aucune autre. Toutefois, les modifications apportées au niveau de la batterie de serveurs Web affectent toutes les collections de sites sur la batterie de serveurs.  
  
 Windows SharePoint Services (WSS) 3.0 vous permet de déployer des solutions uniquement au niveau de la batterie de serveurs, mais [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] vous permet de déployer au niveau de la batterie (solution de batterie) ou de niveau de la collection de sites (solution bac à sable).  
  
## <a name="why-sandboxed-solutions"></a>Pourquoi les Solutions bac à sable ?  
 Dans WSS 3.0, les solutions peut être déployées uniquement au niveau de la batterie de serveurs. Cela signifie que les solutions potentiellement dangereuses ou instabilitées peut être déployées affectées de la batterie de serveurs Web entière et tous les autres collections de sites et applications qui s’exécutent sous ce dernier. Toutefois, grâce aux solutions bac à sable, vous pouvez déployer vos solutions à une sous-zone de la batterie de serveurs, une collection de sites spécifiques. Pour fournir une protection supplémentaire, assembly de la solution n’est pas chargé dans le principal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus (w3wp.exe). Au lieu de cela, il est chargé dans un processus distinct (SPUCWorkerProcess.exe). Ce processus est analysé et implémente des quotas et limitations pour protéger la batterie de serveurs à partir de solutions bac à sable qui effectuent des activités malveillantes, telles que l’exécution de boucles serrées qui consomment des cycles de processeur.  
  
## <a name="site-collection-solution-gallery"></a>Galerie de solutions de Collection de sites  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]2010 offre une fonction qui est appelée « site collection solution bibliothèque ». Vous pouvez accéder à cette fonctionnalité à partir de la page Administration centrale de SharePoint 2010 ou en ouvrant le **Actions du Site** menu, en choisissant **paramètres du Site**, puis en choisissant le **Solutions** lien sous **galeries** dans le site SharePoint. Galeries de solutions constituent des référentiels de solutions qui permettent aux administrateurs de collection de site gérer les solutions dans leurs collections de sites.  
  
 La galerie de solutions est une bibliothèque de documents stockée dans la racine Web du site SharePoint. La galerie de solutions remplace les modèles de site et prend en charge les packages de solution. Quand un fichier de package (.wsp) de solution SharePoint est chargé, il est traité comme une solution bac à sable.  
  
## <a name="sandboxed-solution-limitations"></a>Limitations de la Solution bac à sable  
 Lorsqu’une solution bac à sable est déployée, le tableau des fonctionnalités de SharePoint à sa disposition est limité pour réduire les vulnérabilités de sécurité, qu'il peut avoir. Certaines de ces limitations sont les suivantes :  
  
-   Solutions bac à sable ont un sous-ensemble limité d’éléments de solution déployables à leur disposition. Les modèles de projet SharePoint potentiellement vulnérables, tels que les définitions de site et les flux de travail, ne sont pas disponibles.  
  
-   SharePoint exécute le code de la solution bac à sable dans un processus (SPUCWorkerProcess.exe) distinct à partir de la main [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus d’application pool (w3wp.exe).  
  
-   Dossiers mappés ne peut pas être ajoutés au projet.  
  
-   Types dans le [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft.Office.Server ne peut pas être utilisé dans les solutions bac à sable. En outre, seuls les types dans le [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft.SharePoint peuvent être utilisés dans les solutions bac à sable.  
  
 Il est important de noter ce qui spécifie une solution SharePoint comme une solution bac à sable n’a aucun effet sur le serveur SharePoint. Il détermine uniquement la façon dont le projet SharePoint est déployé sur SharePoint à partir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les assemblys qu’elle est liée à. Il n’affecte pas le fichier .wsp généré et le fichier .wsp ne comporte aucune donnée ayant directement en corrélation avec la *Solution bac à sable* propriété.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Fonctionnalités et des éléments dans les Solutions bac à sable  
 Solutions bac à sable prennent en charge les fonctionnalités et les éléments suivants :  
  
-   Types de contenu/champs  
  
-   Actions personnalisées  
  
-   Flux de travail déclaratifs  
  
-   Récepteurs d’événements  
  
-   Légendes des fonctionnalités  
  
-   Définitions de listes  
  
-   Instances de listes  
  
-   Module et les fichiers  
  
-   Navigation  
  
-   Onet.Xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Prise en charge pour tous les composants WebPart qui dérivent de`System.Web.UI.WebControls.WebParts.WebPart`  
  
-   WebParts  
  
-   Éléments de fonctionnalité WebTemplate (au lieu de Webtemp.xml)  
  
-   Composants Visual Web Parts  
  
 Solutions bac à sable ne prennent pas en charge les fonctionnalités et les éléments suivants :  
  
-   Pages d’application  
  
-   Groupe d’actions personnalisées  
  
-   Fonctionnalités étendues à la batterie de serveurs  
  
-   `HideCustomAction` (élément)  
  
-   Fonctionnalités de portée d’Application Web  
  
-   Flux de travail avec code  
  
## <a name="see-also"></a>Voir aussi  
 [Différences entre le bac à sable et les Solutions de batterie](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  