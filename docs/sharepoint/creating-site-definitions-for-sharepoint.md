---
title: Création de définitions de site pour SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f1a512218c3c1b7af179cfaba3e231a90941fe0
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015059"
---
# <a name="create-site-definitions-for-sharepoint"></a>Créer des définitions de site pour SharePoint
  Le projet de définition de site SharePoint dans vous [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] permet de créer une *définition de site*, qui sert de base pour un nouveau site SharePoint. Ces définitions déterminent non seulement l’apparence et le comportement du site SharePoint, mais également son contenu et ses fonctionnalités par défaut. Dans la définition, vous pouvez placer des listes préconfigurées, des types de contenu, des récepteurs d’événements, des images et d’autres éléments. SharePoint comprend des définitions de site telles que le BLOG, par exemple. Lorsque vous créez un site basé sur la définition du site de BLOG, le site contient les listes, les composants WebPart et les autres éléments requis par un site de blog.

 Pour plus d’informations sur les définitions de site, consultez [modèles de site et définitions](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Projets de définition de site
 Les projets de définition de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournissent uniquement les fichiers de base dont un site SharePoint a besoin ; ils ne fournissent pas de fonctionnalités par défaut. Vous devez ajouter des fichiers et du contenu pour fournir les fonctionnalités de votre choix. Vous pouvez créer le site manuellement en créant et en ajoutant les fichiers dont vous avez besoin.

## <a name="feature-stapling"></a>Association de fonctionnalités
 L’un des avantages de la création de définitions de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] est qu’ils utilisent automatiquement l' *Association de fonctionnalités*. L’Association de fonctionnalités attache une fonctionnalité à une définition de site au lieu d’incorporer ses fonctionnalités dans la définition de site elle-même. Cela vous permet d’ajouter la fonctionnalité à n’importe quel site créé à l’aide de la définition de site sans modifier la définition du site d’origine. Pour plus d’informations, consultez [Association de fonctionnalités](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Composants du projet de définition de site
 Lorsque vous créez une solution de définition de site, les fichiers par défaut suivants sont ajoutés à son nœud **SiteDefinition** .

|Nom de fichier|Description|
|---------------|-----------------|
|*default. aspx*|Page d’hébergement ASPX par défaut pour le nouveau site SharePoint.|
|*onet.xml*|Spécifie la configuration du nouveau site, les composants du modèle de définition de site et le comportement par défaut. Ces paramètres peuvent inclure des attributs tels que les types de contenu activés, les affichages de liste par défaut, les fichiers de modèles de document et les composants WebPart inclus dans le site. Par défaut, la `Modules` section répertorie les fichiers à ajouter au site SharePoint et la façon dont ils sont configurés.|
|*webtemp_ \<SiteDefinitionName> . Xml*|Spécifie les configurations de définition de site qui s’affichent dans la section **sélection du modèle** de la page **nouveau site SharePoint** .|

 Par défaut, toutes les définitions de site sont stockées dans le dossier * \<drive:> \Program Files\Common Files\Microsoft Shared\web server extensions\14\TEMPLATE\SiteTemplates* Chaque définition de site a son propre sous-dossier.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Procédure pas à pas : création d'un projet de définition de site de base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Vous guide pas à pas dans la création d’un projet de définition de site de base dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Comment : créer une définition de site personnalisée et une configuration](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Décrit comment créer une définition de site personnalisée dans SharePoint en copiant une définition de site existante, puis en modifiant la copie.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Décrit le fichier d’origine qui spécifie les définitions de site disponibles dans la section **sélection du modèle** de la page **nouveau site SharePoint** .|
|[Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Décrit comment préparer vos solutions SharePoint pour une utilisation globale.|
|[Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Décrit comment vous pouvez créer des parties d’une page SharePoint que les utilisateurs peuvent modifier.|
|[Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Décrit comment créer des contrôles réutilisables qui s’exécutent dans des pages d’application et des composants WebPart.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Décrit comment utiliser le concepteur qui s’affiche lorsque vous ouvrez une page Web dans votre projet.|
|[Présentation de pages Web ASP.NET](/previous-versions/aspnet/428509ah(v=vs.100))|Fournit des informations générales sur la structure des [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages Web, sur le mode de traitement des pages et sur la [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] manière dont les [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages affichent le balisage conforme aux normes XHTML.|
|[Syntaxe de la page Web ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Décrit les éléments de balisage qui composent une page ASP.NET.|
|[Pages Web ASP.NET de programmation](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Fournit des informations sur la création de gestionnaires d’événements dans [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] les pages et sur l’utilisation du script client.|
|[Programmation dans Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Décrit comment utiliser le modèle objet managé fourni dans [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
