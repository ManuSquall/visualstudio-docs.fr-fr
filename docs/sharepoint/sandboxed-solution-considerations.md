---
title: Considérations sur les solutions bac à sable (sandbox) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839494"
---
# <a name="sandboxed-solution-considerations"></a>Considérations sur les solutions bac à sable
  Les *solutions bac à sable (sandbox)* sont une fonctionnalité de Microsoft SharePoint 2010 qui permet aux utilisateurs de collections de sites de télécharger leurs propres solutions de code personnalisées. Une solution bac à sable (sandbox) courante est que les utilisateurs chargent leurs propres composants WebPart.

 Une application SharePoint bac à sable (sandbox) s’exécute dans un processus contrôlé et sécurisé qui a accès à une partie limitée de la batterie de serveurs Web. Microsoft SharePoint 2010 utilise une combinaison de fonctionnalités, de galeries de solutions, d’analyse de solution et d’une infrastructure de validation pour activer les solutions sandbox.

## <a name="specify-project-trust-level"></a>Spécifier le niveau de confiance du projet
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prend en charge les solutions sandbox via une propriété de projet booléenne appelée *solution bac à sable (sandbox)*. Cette propriété peut être définie à tout moment dans le projet, ou elle peut être spécifiée lors de la création du projet dans l' **Assistant Personnalisation de SharePoint**.

> [!NOTE]
> La modification de la propriété de *solution bac à sable (sandbox)* d’un projet après sa création peut entraîner des erreurs de validation.

 La solution est considérée comme une solution étendue à la batterie si la propriété de la *solution bac à sable (sandbox)* a la valeur **false** ou si vous choisissez l’option **déployer en tant que solution de batterie** . Toutefois, la solution est traitée différemment d’une solution de batterie de serveurs si la propriété de la *solution bac à sable (sandbox)* a la valeur **true** ou si vous choisissez l’option **déployer en tant que solution bac à sable (sandbox)** dans l’Assistant.

## <a name="sharepoint-site-hierarchy"></a>Hiérarchie de site SharePoint
 Pour comprendre le fonctionnement des solutions bac à sable (sandbox), il est utile de savoir que les sites SharePoint sont hiérarchiques dans l’étendue. L’élément supérieur est connu sous le nom de batterie de serveurs Web et d’autres éléments y sont subordonnés :

 Batterie de serveurs web

 Application Web A

 Collection de sites a1

 A1A de site

 Application Web B

 Collection de sites B1

 B1a de site

 B1b de site

 Collection de sites B2

 B2a de site

 Comme vous pouvez le voir, les batteries de serveurs Web peuvent contenir une ou plusieurs applications Web, qui peuvent à leur tour contenir une ou plusieurs collections de sites, qui peuvent avoir des sous-sites, etc. Les modifications apportées à une collection de sites affectent uniquement cette collection de sites et aucune autre. Toutefois, les modifications apportées au niveau de la batterie de serveurs Web affectent toutes les collections de sites de la batterie de serveurs.

 Windows SharePoint Services (WSS) 3,0 vous permet de déployer des solutions uniquement au niveau de la batterie de serveurs, mais [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] vous permet de procéder au déploiement au niveau de la batterie de serveurs (solution de batterie) ou au niveau de la collection de sites (solution bac à sable (sandbox)).

## <a name="why-sandboxed-solutions"></a>Pourquoi les solutions bac à sable (sandbox) ?
 Dans WSS 3,0, les solutions pouvaient être déployées uniquement au niveau de la batterie de serveurs. Cela signifiait que des solutions potentiellement nuisibles ou déstabilisantes pouvaient être déployées et affectent l’ensemble de la batterie de serveurs Web et toutes les autres collections de sites et applications qui s’y exécutent. Toutefois, en utilisant des solutions bac à sable (sandbox), vous pouvez déployer vos solutions dans une sous-zone de la batterie de serveurs, une collection de sites spécifique. Pour fournir une protection supplémentaire, l’assembly de la solution n’est pas chargé dans le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus principal (*w3wp.exe*). Au lieu de cela, il est chargé dans un processus séparé (*SPUCWorkerProcess.exe*). Ce processus est analysé et met en œuvre des quotas et une limitation pour protéger la batterie des solutions sandbox qui effectuent des activités néfastes, telles que l’exécution de boucles serrées qui consomment des cycles de processeur.

## <a name="site-collection-solution-gallery"></a>Galerie de solutions de collection de sites
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 dispose d’une fonctionnalité appelée « Galerie de solutions de collection de sites ». Vous pouvez accéder à cette fonctionnalité à partir de la page Administration centrale de SharePoint 2010 ou en ouvrant le menu **actions du site** , en choisissant **paramètres du site**, puis en choisissant le lien **solutions** sous  **galeries** dans le site SharePoint. Les galeries de solutions sont des référentiels de solutions qui permettent aux administrateurs de collections de sites de gérer des solutions dans leurs collections de sites.

 La Galerie de solutions est une bibliothèque de documents stockée sur le site Web racine du site SharePoint. La Galerie de solutions remplace les modèles de site et prend en charge les packages de solution. Lorsqu’un fichier de package de solution SharePoint (*. wsp*) est chargé, il est traité comme une solution bac à sable (sandbox).

## <a name="sandboxed-solution-limitations"></a>Limitations de la solution bac à sable (sandbox)
 Lors du déploiement d’une solution bac à sable (sandbox), le tableau des fonctionnalités SharePoint disponibles est limité afin de réduire les failles de sécurité qu’elle peut avoir. Voici quelques-unes de ces limitations :

- Les solutions bac à sable (sandbox) ont un sous-ensemble restreint d’éléments de solution déployables disponibles. Les modèles de projet SharePoint potentiellement vulnérables, tels que les définitions de site et les flux de travail, ne sont pas disponibles.

- SharePoint exécute le code de la solution bac à sable (sandbox) dans un processus (*SPUCWorkerProcess.exe*) distinct du processus principal du [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications (*w3wp.exe*).

- Les dossiers mappés ne peuvent pas être ajoutés au projet.

- Les types de l' [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft. Office. Server ne peuvent pas être utilisés dans les solutions bac à sable (sandbox). En outre, seuls les types de l' [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft. SharePoint peuvent être utilisés dans les solutions bac à sable (sandbox).

  Il est important de noter que la spécification d’une solution SharePoint en tant que solution bac à sable (sandbox) n’a aucun effet sur le serveur SharePoint. il détermine uniquement comment le projet SharePoint est déployé sur SharePoint à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les assemblys auxquels il est lié. Elle n’affecte pas le fichier *. wsp* généré, et le fichier *. wsp* n’a pas de données corrélées directement à la propriété de la *solution bac à sable (sandbox)* .

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Fonctionnalités et éléments dans les solutions bac à sable (sandbox)
 Les solutions bac à sable (sandbox) prennent en charge les fonctionnalités et les éléments suivants :

- Types de contenu/champs

- Actions personnalisées

- Flux de travail déclaratifs

- Récepteurs d’événements

- Légendes des fonctionnalités

- Liste des définitions

- Instances de listes

- Module/fichiers

- Navigation

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Prise en charge de tous les composants WebPart qui dérivent de `System.Web.UI.WebControls.WebParts.WebPart`

- composants WebPart

- Éléments de fonctionnalité WebTemplate (au lieu de *Webtemp.xml*)

- composants WebPart visuel

  Les solutions bac à sable (sandbox) ne prennent pas en charge les fonctionnalités et les éléments suivants :

- Pages d’application

- Groupe d’actions personnalisé

- Fonctionnalités étendues à la batterie de serveurs

- `HideCustomAction`, élément

- Fonctionnalités étendues à l’application Web

- Flux de travail avec code

## <a name="see-also"></a>Voir aussi
- [Différences entre les solutions sandbox et les solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
