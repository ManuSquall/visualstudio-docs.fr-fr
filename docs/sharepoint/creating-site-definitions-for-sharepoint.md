---
title: Création de définitions de Site pour SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2abf61bbc960e342a395e9c0ff3395ecde852137
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580970"
---
# <a name="create-site-definitions-for-sharepoint"></a>Créer des définitions de site pour SharePoint
  Le projet de définition de Site SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vous permet de créer un *définition de site*, qui sert de base pour un nouveau site SharePoint. Ces définitions déterminent non seulement l’apparence et le comportement du site SharePoint, mais également son contenu par défaut et les fonctionnalités. Dans la définition, vous pouvez placer les listes préconfigurées, des types de contenu, des récepteurs d’événements, des images et d’autres éléments. SharePoint comprend des définitions de site telles que des blogs, par exemple. Lorsque vous créez un site basé sur la définition de site BLOG, le site contient les listes, les composants WebPart et les autres éléments nécessitant un site de création de blogs.

 Pour plus d’informations sur les définitions de site, consultez [modèles de Site et les définitions](http://go.microsoft.com/fwlink/?LinkId=179134).

## <a name="site-definition-projects"></a>Projets de définition de site
 Dans les projets de définition de site [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournissent uniquement les fichiers de base qui a besoin d’un site SharePoint ; ils ne fournissent pas toutes les fonctionnalités par défaut. Vous devez ajouter des fichiers et contenu pour fournir les fonctionnalités que vous souhaitez. Vous pouvez créer le site manuellement, en créant et en ajoutant les fichiers dont vous avez besoin.

## <a name="feature-stapling"></a>Association de fonctions
 L’un des avantages de la création de définitions de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] est qu’ils utilisent automatiquement *agrafage*. L’association de joindre une fonctionnalité à une définition de site au lieu d’incorporer ses fonctionnalités dans la définition de site. Cette opération permet d’ajouter la fonctionnalité à n’importe quel site créé à l’aide de la définition de site sans modification de la définition de site d’origine. Pour plus d’informations, consultez [agrafage](http://go.microsoft.com/fwlink/?LinkID=119283).

## <a name="site-definition-project-components"></a>Composants de projet de définition de site
 Lorsque vous créez une solution de définition de site, les fichiers par défaut suivants sont ajoutés à son **SiteDefinition** nœud.

|Nom du fichier|Description|
|---------------|-----------------|
|*default.aspx*|La page d’accueil ASPX par défaut pour le nouveau site SharePoint.|
|*onet.xml*|Spécifie la configuration du nouveau site, les composants du modèle de définition de site et le comportement par défaut. Ces paramètres peuvent inclure des attributs tels que les types de contenu qui sont activées, les affichages de liste par défaut, les fichiers de modèle de document et les composants inclus avec le site Web. Par défaut, le `Modules` section répertorie les fichiers à ajouter au site SharePoint et la façon dont ils sont configurés.|
|*webtemp_\<SiteDefinitionName>.xml*|Spécifie les configurations de définition de site qui s’affiche dans le **sélection du modèle** section de la **nouveau SharePoint Site** page.|

 Par défaut, toutes les définitions de site sont stockées dans le  *\<lecteur : > \Program Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* dossier. Chaque définition de site a son propre sous-dossier.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Procédure pas à pas : Créer un projet de définition de Site de base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Comment procéder, étape par étape la création d’un projet de définition de site de base dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Guide pratique pour Créer une définition de Site personnalisée et une Configuration](http://go.microsoft.com/fwlink/?LinkId=183309)|Décrit comment créer une définition de site personnalisée dans SharePoint en copiant une définition de site existante, puis en modifiant la copie.|
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Décrit le fichier d’origine qui spécifie les définitions de site disponibles dans le **sélection du modèle** section de la **nouveau SharePoint Site** page.|
|[Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Décrit comment préparer vos solutions SharePoint dans le monde entier.|
|[Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Décrit comment vous pouvez créer des parties d’une page SharePoint que les utilisateurs peuvent modifier.|
|[Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Décrit comment vous pouvez créer des contrôles réutilisables qui s’exécutent dans les pages d’application et les composants WebPart.|
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Décrit comment utiliser le concepteur qui s’affiche lorsque vous ouvrez une page Web dans votre projet.|
|[Vue d’ensemble des Pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Fournit des informations générales sur la structure des [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] des pages Web, mode de traitement des pages par [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]et comment [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] balisage conforme aux normes XHTML les pages s’affichent.|
|[Syntaxe de Page Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Décrit les éléments de balisage qui composent une page ASP.NET.|
|[Programmation des Pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Fournit des informations sur la création de gestionnaires d’événements dans [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages et comment travailler avec le script client.|
|[Programmation dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Décrit comment utiliser le modèle objet managé qui est fourni dans [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
