---
title: "Création d’élément modèles et des modèles de projet pour les éléments de projet SharePoint | Documents Microsoft"
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
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7ea1c76cda46313458dcac01b415e7541732a26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>Création de modèles d'élément et de modèles de projet pour les éléments de projet SharePoint
  Lorsque vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez l’associer avec un modèle d’élément ou un modèle de projet afin que les autres développeurs peuvent utiliser l’élément de projet dans Visual Studio. Vous pouvez également créer un Assistant pour le modèle.  
  
 Par exemple, Visual Studio n’inclut pas un modèle de projet ou un modèle d’élément pour l’ajout d’un champ à un site SharePoint. Vous pouvez définir un type d’élément de projet SharePoint qui représente un champ et puis construire un modèle d’élément autres développeurs peuvent utiliser pour ajouter l’élément de champ à un projet SharePoint. Ou bien, vous pouvez construire un modèle de projet afin que les développeurs peuvent créer un nouveau projet SharePoint qui contient l’élément de champ. Dans les deux cas, vous pouvez également fournir un Assistant qui s’affiche lorsque les développeurs utilisent votre modèle. Cet Assistant peut collecter des informations à partir d’aux développeurs de configurer le nouvel élément ou le projet.  
  
 Modèles d’élément et les modèles de projet sont des fichiers .zip qui contiennent les fichiers qui sont utilisés par Visual Studio pour créer un élément de projet ou le projet. Pour plus d’informations sur les notions de base des modèles d’élément et les modèles de projet, consultez [création de modèles de projet et élément](/visualstudio/ide/creating-project-and-item-templates).  
  
##  <a name="creatingitemtemplates"></a>Création de modèles d’élément  
 Lorsque vous créez un modèle d’élément pour un élément de projet SharePoint, il existe certains fichiers sont toujours requis et les fichiers facultatifs qui peuvent être utilisées par certains types d’éléments de projet. Pour une procédure pas à pas qui montre comment définir un type d’élément de projet SharePoint et créer un modèle d’élément pour celle-ci, consultez [procédure pas à pas : création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Le tableau suivant répertorie les fichiers requis pour créer un modèle d’élément pour un élément de projet SharePoint.  
  
|Fichier obligatoire|Description|  
|-------------------|-----------------|  
|Un fichier .spdata|Il s’agit d’un fichier XML qui spécifie le contenu et le comportement par défaut de l’élément de projet. Ce fichier doit être inclus dans le modèle d’élément. Pour plus d’informations sur le contenu des fichiers .spdata, consultez [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Un fichier .vstemplate.|Ce fichier fournit à Visual Studio avec les informations requises pour afficher le modèle dans le **ajouter un nouvel élément** boîte de dialogue et créer un élément de projet à partir du modèle. Ce fichier doit être inclus dans le modèle d’élément. Pour plus d’informations, consultez [fichiers métadonnées de modèle Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un assembly d’extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface.|Cet assembly définit le comportement de l’exécution de l’élément de projet. Cet assembly doit être inclus dans le package VSIX avec le modèle d’élément. Pour plus d’informations, consultez [Types d’éléments de projet de définition personnalisé SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) et [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 Le tableau suivant répertorie certains des fichiers facultatifs courants qui peuvent être inclus dans le modèle d’élément. Certains types d’éléments de projet peuvent nécessiter d’autres fichiers non répertoriées ici.  
  
|Fichier facultatif|Description|  
|-------------------|-----------------|  
|Elements.Xml|A *élément Feature* fichier. Ce fichier définit l’interface utilisateur et le comportement de la personnalisation créée par l’élément de projet. Chaque type de personnalisation, telles que les instances de listes, les types de contenu ou les actions personnalisées, a un schéma différent qui définit le contenu de ce fichier. Pour plus d’informations, consultez [bloc de construction : fonctionnalités](http://go.microsoft.com/fwlink/?LinkId=169183) et [schémas](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.Xml|Le fichier de schéma pour les définitions de liste. Pour plus d’informations, consultez [bloc de construction : listes et bibliothèques de documents](http://go.microsoft.com/fwlink/?LinkId=177792) et [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|.WebPart|A *définition WebPart* fichier. Ce fichier contient des paramètres de propriété pour un composant WebPart. Pour plus d’informations, consultez [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|.ascx|Un fichier de contrôle utilisateur ASP.NET. Ce fichier définit l’interface utilisateur d’un composant Visual Web Part.|  
|.aspx|Un fichier de page ASP.NET. Ce fichier contient le balisage XML qui définit une page d’application.|  
|fichiers .cs ou .vb|Ces fichiers de code définissent le comportement des personnalisations de SharePoint qui ont un modèle de programmation qui est accessible à partir de Visual c# ou de code Visual Basic, telles que les pages d’application, les composants WebPart et les workflows.|  
  
## <a name="creating-project-templates"></a>Création de modèles de projet  
 Lorsque vous créez un modèle de projet SharePoint, il existe certains fichiers sont toujours les fichiers requis et facultatifs qui peuvent être utilisées par certains types de projets. En règle générale, les projets SharePoint incluent au moins un élément de projet SharePoint. Toutefois, cela n’est pas nécessaire. Par exemple, vous pouvez définir un modèle de projet SharePoint qui est destiné à être utilisée que pour déployer des solutions SharePoint créées dans d’autres projets.  
  
 Pour une procédure pas à pas qui montre comment définir un type d’élément de projet SharePoint et créer un modèle de projet pour celle-ci, consultez [procédure pas à pas : création d’un élément de projet colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Le tableau suivant répertorie les fichiers qui doivent être inclus dans un modèle de projet SharePoint.  
  
|Fichier obligatoire|Description|  
|-------------------|-----------------|  
|Un fichier .vstemplate|Ce fichier fournit à Visual Studio avec les informations requises pour afficher le modèle dans le **nouveau projet** boîte de dialogue et créer un projet à partir du modèle. Pour plus d’informations, consultez [fichiers métadonnées de modèle Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un fichier .csproj ou .vbproj|Il s’agit du fichier projet. Il définit le contenu et les paramètres de configuration du projet.|  
|Package|Ce fichier définit le package de déploiement pour le projet. Lorsque vous utilisez le Concepteur de packages pour personnaliser le package de solution pour votre projet, Visual Studio stocke les données sur le package de solution dans ce fichier.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d’inclure uniquement le contenu du fichier de package au minimum, et de configurer le package de solution à l’aide de l’API dans le <xref:Microsoft.VisualStudio.SharePoint.Packages> espace de noms dans une extension associé au modèle de projet. Dans ce cas, votre modèle de projet est protégé contre les futures modifications de la structure du fichier de package. Pour obtenir un exemple qui montre comment créer un fichier de package avec uniquement le minimum requis, le contenu, consultez [procédure pas à pas : création d’un élément de projet colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier le fichier de package directement, vous pouvez vérifier le contenu en utilisant le schéma dans %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd.|  
|Package.Template.xml|Ce fichier fournit la base pour le fichier manifeste de solution (manifest.xml) pour le package de solution SharePoint (.wsp) qui est généré à partir du projet. Vous pouvez ajouter du contenu à ce fichier si vous souhaitez spécifier un comportement qui n’est pas destiné à être modifié par les utilisateurs de votre type de projet. Pour plus d’informations, consultez [bloc de construction : Solutions](http://go.microsoft.com/fwlink/?LinkId=169186) et [schéma de la Solution](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Lorsque vous générez un package de solution du projet, Visual Studio fusionne le contenu du package et les fichiers Package.Template.xml dans la solution dans le fichier de manifeste. Pour plus d’informations sur la création de packages de solution, consultez [Comment : créer un Package de Solution SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 Le tableau suivant répertorie les fichiers facultatif qui peuvent être inclus dans le modèle de projet.  
  
|Fichier facultatif|Description|  
|-------------------|-----------------|  
|éléments de projet SharePoint|Vous pouvez inclure un ou plusieurs fichiers .spdata qui définissent les types d’éléments de projet SharePoint. Chaque fichier .spdata doit avoir une correspondance <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation dans un assembly d’extension qui est inclus dans le package VSIX avec le modèle de projet. Pour plus d’informations, consultez [création de modèles d’élément](#creatingitemtemplates).<br /><br /> En règle générale, les projets SharePoint incluent au moins un élément de projet SharePoint. Toutefois, cela n’est pas nécessaire.|  
|*featureName*.feature|Ce fichier définit une fonctionnalité SharePoint qui permet de regrouper plusieurs éléments de projet pour le déploiement. Lorsque vous utilisez le Concepteur de fonctionnalités pour personnaliser une fonctionnalité dans votre projet, Visual Studio stocke les données relatives à la fonctionnalité de ce fichier. Si vous souhaitez regrouper les éléments de projet différentes fonctionnalités, vous pouvez inclure plusieurs fichiers .feature.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d’inclure uniquement le contenu obligatoire minimum dans chaque fichier .feature, et configurer les fonctionnalités à l’aide de l’API dans le <xref:Microsoft.VisualStudio.SharePoint.Features> espace de noms dans une extension qui est associée à la modèle de projet. Dans ce cas, votre modèle de projet est protégé contre les futures modifications de la structure du fichier .feature. Pour obtenir un exemple qui montre comment créer un fichier .feature avec uniquement le minimum requis, le contenu, consultez [procédure pas à pas : création d’un élément de projet colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier un fichier .feature directement, vous pouvez vérifier le contenu en utilisant le schéma dans %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd.|  
|*featureName*. Template.Xml|Ce fichier fournit la base pour le fichier de manifeste de fonctionnalité (Feature.xml) pour chaque fonctionnalité qui est générée à partir du projet. Vous pouvez ajouter du contenu à ce fichier si vous souhaitez spécifier un comportement qui n’est pas destiné à être modifié par les utilisateurs de votre type de projet. Pour plus d’informations, consultez [bloc de construction : fonctionnalités](http://go.microsoft.com/fwlink/?LinkId=169183) et [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) fichiers.<br /><br /> Lorsque vous générez un package de solution du projet, Visual Studio fusionne le contenu de chaque paire de *featureName*fichier .feature et *featureName*. Template.XML dans un fichier de manifeste de fonctionnalité. Pour plus d’informations sur la création de packages de solution, consultez [Comment : créer un Package de Solution SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## <a name="creating-wizards-for-item-templates-and-project-templates"></a>Création d’Assistants pour les modèles d’élément et les modèles de projet  
 Une fois que vous définissez un type d’élément de projet SharePoint et l’associez à un modèle d’élément ou un projet, vous pouvez également créer un Assistant. L’Assistant affiche lorsqu’un développeur utilise le modèle d’élément pour ajouter l’élément de projet SharePoint à un projet, ou lorsqu’un développeur utilise le modèle de projet pour créer un projet qui contient l’élément de projet SharePoint. L’Assistant peut être utilisé pour collecter des informations à partir de développeurs et à initialiser le nouvel élément de projet SharePoint.  
  
 Pour les procédures pas à pas qui montrent comment créer des Assistants pour les modèles d’élément et les modèles de projet, consultez [procédure pas à pas : création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) et [procédure pas à pas : création d’un Site Élément de projet colonne avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Types d’éléments de projet SharePoint personnalisé](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procédure pas à pas : Création d’un élément de projet de colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procédure pas à pas : Création d’un élément de projet de colonne de Site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Création de modèles de projet et d’élément](/visualstudio/ide/creating-project-and-item-templates)  
  
  