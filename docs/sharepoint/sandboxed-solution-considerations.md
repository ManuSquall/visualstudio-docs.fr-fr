---
title: Considérations relatives à la Solution bac à sable | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f6345e7627549c672aa28fac8cba5f6d9658a23
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435447"
---
# <a name="sandboxed-solution-considerations"></a>Considérations relatives à la solution bac à sable
  *Solutions bac à sable* sont une fonctionnalité de Microsoft SharePoint 2010 qui permet aux utilisateurs de collection de sites de télécharger leurs propres solutions de code personnalisé. Une solution bac à sable courante est les utilisateurs de télécharger leurs propres composants WebPart.

 Une application SharePoint sandbox s’exécute dans un processus sécurisé et surveillé qui a accès à une partie limitée de la batterie de serveurs Web. Microsoft SharePoint 2010 utilise une combinaison de fonctionnalités, des galeries de solution, solution de surveillance et une infrastructure de validation pour activer les solutions sandbox.

## <a name="specify-project-trust-level"></a>Spécifiez le niveau de confiance de projet
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prend en charge les solutions bac à sable via une propriété de projet booléenne appelées *Solution bac à sable*. Cette propriété peut être définie à tout moment dans le projet, ou il peut être spécifié lorsque vous créez le projet dans le **Assistant Personnalisation de SharePoint**.

> [!NOTE]
> Modification de la *Solution bac à sable* propriété d’un projet après sa création peut entraîner des erreurs de validation.

 La solution est considérée comme une solution de batterie si le *Solution bac à sable* propriété est définie sur **false** ou si vous choisissez la **déployer en tant que solution de batterie** option. Toutefois, la solution est traitée différemment d’une solution de batterie de serveurs si le *Solution bac à sable* propriété est définie sur **true** ou si vous choisissez la **déployer en tant que sandboxed solution** option de l’Assistant.

## <a name="sharepoint-site-hierarchy"></a>Hiérarchie de site SharePoint
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

 Comme vous pouvez le voir, les batteries de serveurs Web peuvent contenir une ou plusieurs applications Web, qui à son tour peuvent contenir un ou plusieurs collections de sites, ce qui peuvent avoir des sous-sites et ainsi de suite. Modifications apportées à une collection de sites concernent uniquement que collection de sites et aucune autre. Toutefois, les modifications apportées au niveau de batterie de serveurs Web affectent toutes les collections de sites sur la batterie de serveurs.

 Windows SharePoint Services (WSS) 3.0 vous permet de déployer des solutions uniquement au niveau de la batterie de serveurs, mais [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] vous permet de déployer sur le niveau de la batterie (solution de batterie) ou le niveau de collection de sites (solution bac à sable).

## <a name="why-sandboxed-solutions"></a>Pourquoi les solutions sable ?
 Dans WSS 3.0, les solutions peut être déployées uniquement au niveau de la batterie. Cela signifiait que les solutions potentiellement dangereuses ou déstabilisants peut être déployées affectés de la batterie de serveurs Web entière et tous les autres collections de sites et applications qui s’exécutent sous ce dernier. Toutefois, à l’aide de solutions sandbox, vous pouvez déployer vos solutions à une sous-zone de la batterie de serveurs, une collection de sites spécifiques. Pour fournir une protection supplémentaire, assembly de la solution n’est pas chargé dans la main [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus (*w3wp.exe*). Au lieu de cela, il est chargé dans un processus séparé (*SPUCWorkerProcess.exe*). Ce processus est analysé et implémente des quotas et limitations pour protéger la batterie de serveurs à partir de solutions sandbox qui effectuent des activités malveillantes, telles que l’exécution des boucles serrées qui consomment des cycles de processeur.

## <a name="site-collection-solution-gallery"></a>Galerie de solutions de collection de sites
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 propose une fonctionnalité qui est appelée la « site collection galerie de solutions. » Vous pouvez accéder à cette fonctionnalité à partir de la page Administration centrale de SharePoint 2010 ou en ouvrant le **Actions du Site** menu, en choisissant **paramètres du Site**, puis en choisissant le **Solutions** situé sous **galeries** dans le site SharePoint. Galeries de solutions sont des référentiels de solutions qui permettent aux administrateurs de collection de site gérer des solutions dans leurs collections de sites.

 La galerie de solutions est une bibliothèque de documents stockée dans la racine Web du site SharePoint. La galerie de solutions remplace les modèles de site et prend en charge les packages de solution. Lorsqu’un package de solution SharePoint (*.wsp*) fichier est chargé, il est traité comme une solution bac à sable.

## <a name="sandboxed-solution-limitations"></a>Limitations de la solution bac à sable
 Lorsqu’une solution bac à sable est déployée, le tableau des fonctionnalités de SharePoint à sa disposition est limité pour réduire les vulnérabilités de sécurité, qu'elle peut avoir. Certaines de ces restrictions sont les suivantes :

- Les solutions sandbox. vous ont un sous-ensemble limité d’éléments de solution pouvant être déployée à leur disposition. Les modèles de projet SharePoint potentiellement vulnérables, tels que les définitions de site et les flux de travail, ne sont pas disponibles.

- SharePoint exécute le code de la solution bac à sable dans un processus (*SPUCWorkerProcess.exe*) distinct à partir de la main [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications (*w3wp.exe*) processus.

- Dossiers mappés ne peut pas être ajoutés au projet.

- Types dans le [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft.Office.Server ne peut pas être utilisé dans les solutions sandbox. En outre, seuls les types dans le [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft.SharePoint peuvent être utilisés dans les solutions sandbox.

  Il est important de noter que si vous spécifiez une solution SharePoint comme une solution bac à sable n’a aucun effet sur le serveur SharePoint. Il détermine uniquement comment le projet SharePoint est déployé sur SharePoint à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les assemblys qu’il se lie au. Il n’affecte pas le texte généré *.wsp* fichier et le *.wsp* fichier ne comporte aucune donnée directement en corrélation avec la *Solution bac à sable* propriété.

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Éléments dans les solutions sandbox et des fonctions
 Solutions bac à sable prennent en charge les fonctionnalités et les éléments suivants :

- Types de contenu/champs

- Actions personnalisées

- Flux de travail déclaratifs

- Récepteurs d’événements

- Légendes des fonctionnalités

- Définitions de listes

- Instances de listes

- Module/fichiers

- Navigation

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Prise en charge pour tous les composants WebPart qui dérivent de `System.Web.UI.WebControls.WebParts.WebPart`

- WebParts

- Éléments de fonctionnalité WebTemplate (au lieu de *Webtemp.xml*)

- Composants Visual Web Parts

  Solutions bac à sable ne prennent pas en charge les fonctionnalités et les éléments suivants :

- Pages d’application

- Groupe d’actions personnalisées

- Fonctionnalités étendues à la batterie de serveurs

- `HideCustomAction`, élément

- Fonctionnalités de portée d’Application Web

- Flux de travail avec code

## <a name="see-also"></a>Voir aussi
- [Différences entre le bac à sable et les solutions de batterie](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
