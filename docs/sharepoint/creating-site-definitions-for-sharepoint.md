---
title: "Création de définitions de Site pour SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d29ab819dfc7efd04d27652ab3d711c89045847c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="creating-site-definitions-for-sharepoint"></a>Création de définitions de site pour SharePoint
  Le projet de définition de Site SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vous permet de créer un *définition du site*, qui sert de base pour un site SharePoint. Ces définitions de déterminent non seulement l’apparence et le comportement du site SharePoint, mais également son contenu par défaut et les fonctionnalités. Dans la définition, vous pouvez placer des listes préconfigurées, des types de contenu, des récepteurs d’événements, des images et d’autres éléments. SharePoint inclut des définitions de site, tels que des blogs, par exemple. Lorsque vous créez un site basé sur la définition de site BLOG, le site contient les listes, les composants WebPart et les autres éléments nécessitant un site de création de blogs.  
  
 Pour plus d’informations sur les définitions de site, consultez [les modèles de Site et les définitions](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Projets de définition de site  
 Dans les projets de définition de site [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournissent uniquement les fichiers de base qui a besoin d’un site SharePoint ; ils ne fournissent pas toutes les fonctionnalités par défaut. Vous devez ajouter des fichiers et contenu pour fournir les fonctionnalités que vous souhaitez. Vous pouvez générer le site manuellement, en créant et en ajoutant les fichiers dont vous avez besoin.  
  
## <a name="feature-stapling"></a>Association de fonctions  
 L’un des avantages de la création de définitions de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] est qu’ils utilisent automatiquement le *agrafage*. L’association de joindre une fonctionnalité à une définition de site au lieu d’incorporer ses fonctionnalités dans la définition de site. Cela vous permet d’ajouter la fonctionnalité à n’importe quel site créé à l’aide de la définition de site sans modification de la définition de site d’origine. Pour plus d’informations, consultez [agrafage](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Composants de projet de définition de site  
 Lorsque vous créez une solution de définition de site, les fichiers par défaut suivants sont ajoutés à ses **SiteDefinition** nœud.  
  
|Nom du fichier|Description|  
|---------------|-----------------|  
|default.aspx|La page d’accueil ASPX par défaut pour le nouveau site SharePoint.|  
|Onet.Xml|Spécifie la configuration du nouveau site, les composants du modèle de définition de site et le comportement par défaut. Ces paramètres peuvent inclure des attributs, tels que les types de contenu qui sont activés, les affichages de liste par défaut, les fichiers de modèle de document et composants inclus avec le site Web. Par défaut, le `Modules` section répertorie les fichiers à ajouter au site SharePoint et la façon dont ils sont configurés.|  
|webtemp_*SiteDefinitionName*.xml|Spécifie les configurations de définition de site qui s’affiche dans le **sélection du modèle** section de la **nouveau SharePoint Site** page.|  
  
 Par défaut, toutes les définitions de site sont stockées dans le *lecteur :*\Program Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates dossier. Chaque définition de site possède son propre sous-dossier.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : création d’un projet de définition de site de base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Montre comment la création d’un projet de définition de site de base dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Comment : créer une définition de Site personnalisée et une Configuration](http://go.microsoft.com/fwlink/?LinkId=183309)|Décrit comment créer une définition de site personnalisée dans SharePoint en copiant une définition de site existante, puis modifiez par la suite.|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|Décrit le fichier d’origine qui spécifie les définitions de site disponibles dans le **sélection du modèle** section de la **nouveau SharePoint Site** page.|  
|[Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Décrit comment préparer vos solutions SharePoint dans le monde entier.|  
|[Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Décrit comment vous pouvez créer des parties d’une page SharePoint que les utilisateurs peuvent modifier.|  
|[Création de contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Décrit comment vous pouvez créer des contrôles réutilisables qui s’exécutent dans les pages d’application et les composants WebPart.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Décrit comment utiliser le concepteur qui s’affiche lorsque vous ouvrez une page Web dans votre projet.|  
|[Vue d’ensemble des Pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Fournit des informations générales sur la structure des [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] des pages Web, mode de traitement des pages par [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]et comment [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages affichent un balisage conforme aux normes XHTML.|  
|[Syntaxe des pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Décrit les éléments de balisage qui composent une page ASP.NET.|  
|[Programmation des Pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Fournit des informations sur la création de gestionnaires d’événements dans [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages et comment travailler avec un script client.|  
|[Programmation dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Décrit comment utiliser le modèle objet managé qui est fourni dans [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  