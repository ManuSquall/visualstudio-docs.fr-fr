---
title: "Creating Item Templates and Project Templates for SharePoint Project Items | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  Lorsque vous définissez un type d'élément de projet SharePoint personnalisé, vous pouvez l'associer à un modèle d'élément ou un modèle de projet de façon à le mettre à la disposition d'autres développeurs dans Visual Studio.  Vous pouvez également créer un Assistant pour le modèle.  
  
 Par exemple, Visual Studio n'inclut pas de modèle de projet ou un modèle d'élément pour ajouter un champ à un site SharePoint.  Vous pouvez définir un type d'élément de projet SharePoint qui représente un champ, puis construire un modèle d'élément que d'autres développeurs peuvent utiliser pour ajouter l'élément de champ à un projet SharePoint.  Sinon, vous pouvez construire un modèle de projet afin que les développeurs puissent créer un projet SharePoint qui contient l'élément de champ. Dans les deux cas, vous pouvez également fournir un assistant qui s'affiche lorsque les développeurs utilisent votre modèle.  Cet Assistant peut collecter des informations auprès des développeurs pour configurer le nouvel élément ou projet.  
  
 Les modèles d'élément et de projet sont des fichiers .zip qui contiennent les fichiers utilisés par Visual Studio pour créer un élément de projet ou un projet.  Pour plus d'informations sur les notions de base des modèles d'élément et de projet, consultez [Création de modèles de projets et d'éléments personnalisés dans Visual Studio](../ide/creating-project-and-item-templates.md).  
  
##  <a name="creatingitemtemplates"></a> Création de modèles d'élément  
 Lorsque vous créez un modèle d'élément pour un élément de projet SharePoint, certains fichiers sont toujours requis et certains fichiers facultatifs peuvent être utilisés par certains types d'éléments de projet.  Pour apprendre à définir un type d'élément de projet SharePoint et créer un modèle d'élément pour celui\-ci, étape par étape, consultez [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Le tableau suivant répertorie les fichiers requis pour créer un modèle d'élément pour un élément de projet SharePoint.  
  
|Fichier obligatoire|Description|  
|-------------------------|-----------------|  
|Un fichier .spdata|Il s'agit d'un fichier XML qui spécifie le contenu et le comportement par défaut de l'élément de projet.  Ce fichier doit être inclus dans le modèle d'élément.  Pour plus d'informations sur le contenu des fichiers .spdata, consultez [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Fichier .vstemplate.|Ce fichier fournit à Visual Studio les informations requises pour afficher le modèle dans la boîte de dialogue **Ajouter un nouvel élément** et créer un élément de projet du modèle.  Ce fichier doit être inclus dans le modèle d'élément.  Pour plus d’informations, consultez [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/fr-fr/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Assembly d'extension Visual Studio qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.|Cet assembly définit le comportement au moment de l'exécution de l'élément de projet.  Cet assembly doit être inclus dans le package VSIX avec le modèle d'élément.  Pour plus d'informations, consultez [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md) et [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 Le tableau suivant répertorie certains des fichiers facultatifs les plus courants qui peuvent être inclus dans le modèle d'élément.  Certains types d'éléments de projet peuvent nécessiter d'autres fichiers non indexés ici.  
  
|Fichier facultatif|Description|  
|------------------------|-----------------|  
|Elements.xml|Fichier d'*élément de fonctionnalité*.  Ce fichier définit l'interface utilisateur et le comportement de la personnalisation créée par l'élément de projet.  Chaque type de personnalisation, tel que les instances de listes, les types de contenu ou les actions personnalisées, a un schéma différent qui définit le contenu de ce fichier.  Pour plus d'informations, consultez [Bloc de construction : fonctionnalités \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=169183) et [Schémas de fonctionnalités \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.xml|Fichier de schéma pour les définitions de listes.  Pour plus d'informations, consultez [Bloc de construction : listes et bibliothèques de documents \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177792) et [Schema.xml \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|.webpart|Fichier de *définition de composant WebPart*.  Ce fichier contient des paramètres de propriétés pour un composant WebPart.  Pour plus d'informations, consultez [Bloc de construction : composants WebPart \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|.ascx|Fichier UserControl ASP.NET.  Ce fichier définit l'interface utilisateur d'un composant Visual Web Part.|  
|.aspx|Fichier de page ASP.NET.  Ce fichier contient le balisage XML qui définit une page d'application.|  
|Fichiers .cs ou .vb|Ces fichiers de code définissent le comportement des personnalisations de SharePoint qui ont un modèle de programmation accessible à partir du code Visual C\# ou Visual Basic, comme les pages d'application, les composants WebPart et les flux de travail.|  
  
## Création de modèles de projet  
 Lorsque vous créez un modèle de projet SharePoint, certains fichiers sont toujours requis et d'autres fichiers facultatifs peuvent être utilisés par certains types de projets.  En général, les projets SharePoint incluent au moins un élément de projet SharePoint.  Toutefois, cela n'est pas obligatoire.  Par exemple, vous pouvez définir un modèle de projet SharePoint à n'utiliser que pour déployer des solutions SharePoint créées dans d'autres projets.  
  
 Pour apprendre à définir un type d'élément de projet SharePoint et créer un modèle de projet pour celui\-ci, étape par étape, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Le tableau suivant répertorie les fichiers qui doivent être inclus dans un modèle de projet SharePoint.  
  
|Fichier obligatoire|Description|  
|-------------------------|-----------------|  
|Un fichier .vstemplate|Ce fichier fournit à Visual Studio les informations requises pour afficher le modèle dans la boîte de dialogue **Nouveau projet** et créer un élément de projet du modèle.  Pour plus d’informations, consultez [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/fr-fr/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un fichier .csproj ou .vbproj|Il s'agit du fichier projet.  Il définit le contenu et les paramètres de configuration du projet.|  
|Package.package|Ce fichier définit le package de déploiement pour le projet.  Lorsque vous utilisez le Concepteur de packages afin de personnaliser le package de solution pour votre projet, Visual Studio stocke les données relatives au package de solution dans ce fichier.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d'inclure uniquement le contenu obligatoire minimum dans le fichier Package.package et de configurer le package de solution à l'aide des API dans l'espace de noms <xref:Microsoft.VisualStudio.SharePoint.Packages> dans une extension associée au modèle de projet.  Ainsi, votre modèle de projet est protégé contre les futures modifications de la structure du fichier Package.package.  Pour obtenir un exemple qui montre comment créer un fichier Package.package avec uniquement le contenu obligatoire minimum, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier le fichier Package.package directement, vous pouvez vérifier le contenu en utilisant le schéma dans %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd.|  
|Package.Template.xml|Ce fichier fournit la base pour le fichier manifeste de solution \(manifest.xml\) pour le package de solution SharePoint \(.wsp\) généré à partir du projet.  Vous pouvez ajouter le contenu à ce fichier si vous souhaitez spécifier certains comportements que les utilisateurs de votre type de projet ne sont pas censés modifier.  Pour plus d'informations, consultez [Bloc de construction : solutions \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=169186) et [Schéma de solution \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Lorsque vous générez un package de solution à partir du projet, Visual Studio fusionne le contenu des fichiers Package.package et Package.Template.xml dans le fichier manifeste de la solution.  Pour plus d'informations sur la génération de packages de solutions, consultez [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/fr-fr/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 Le tableau suivant répertorie les fichiers facultatifs qui peuvent être inclus dans le modèle de projet.  
  
|Fichier facultatif|Description|  
|------------------------|-----------------|  
|Éléments de projet SharePoint|Vous pouvez inclure un ou plusieurs fichiers .spdata qui définissent des types d'éléments de projet SharePoint.  Chaque fichier .spdata doit avoir une implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> correspondante dans un assembly d'extension qui est inclus dans le package VSIX avec le modèle de projet.  Pour plus d'informations, consultez [Création de modèles d'élément](#creatingitemtemplates).<br /><br /> En général, les projets SharePoint incluent au moins un élément de projet SharePoint.  Toutefois, cela n'est pas obligatoire.|  
|*NomFonctionnalité*.feature|Ce fichier définit une fonctionnalité SharePoint utilisée afin de regrouper plusieurs éléments de projet pour le déploiement.  Lorsque vous utilisez le Concepteur de fonctionnalités pour personnaliser une fonctionnalité dans votre projet, Visual Studio stocke les données relatives à la fonctionnalité dans ce fichier.  Si vous souhaitez regrouper les éléments de projet dans différentes fonctionnalités, vous pouvez inclure plusieurs fichiers .feature.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d'inclure uniquement le contenu obligatoire minimum dans chaque fichier .feature et de configurer les fonctionnalités à l'aide des API dans l'espace de noms <xref:Microsoft.VisualStudio.SharePoint.Features> dans une extension associée au modèle de projet.  Ainsi, votre modèle de projet est protégé contre les futures modifications de la structure du fichier .feature.  Pour obtenir un exemple qui montre comment créer un fichier .feature avec uniquement le contenu obligatoire minimum, consultez [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier un fichier .feature directement, vous pouvez vérifier le contenu en utilisant le schéma dans %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd.|  
|*NomFonctionnalité*.Template.xml|Ce fichier fournit la base du fichier manifeste de fonctionnalité \(Feature.xml\) pour chaque fonctionnalité générée à partir du projet.  Vous pouvez ajouter le contenu à ce fichier si vous souhaitez spécifier certains comportements que les utilisateurs de votre type de projet ne sont pas censés modifier.  Pour plus d'informations, consultez [Bloc de construction : fonctionnalités \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=169183) et [Feature.xml \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177795).<br /><br /> Lorsque vous générez un package de solution à partir du projet, Visual Studio fusionne le contenu de chaque paire de fichier *NomFonctionnalité*.feature et de fichiers *NomFonctionnalité*.Template.xml dans un fichier manifeste de la fonctionnalité.  Pour plus d'informations sur la génération de packages de solutions, consultez [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/fr-fr/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## Création d'Assistants pour les modèles d'élément et de projet  
 Après avoir défini un type d'élément de projet SharePoint et l'avoir associé à un modèle d'élément ou de projet, vous pouvez également créer un Assistant.  L'Assistant s'affiche lorsqu'un développeur utilise le modèle d'élément pour ajouter l'élément de projet SharePoint à un projet ou lorsqu'il emploie le modèle de projet pour créer un projet contenant l'élément de projet SharePoint.  L'Assistant peut servir à recueillir des informations auprès des développeurs et à initialiser le nouvel élément de projet SharePoint.  
  
 Pour obtenir les procédures pas à pas expliquant comment créer des Assistants pour les modèles d'élément et de projet, consultez [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) et [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Voir aussi  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Création de modèles de projets et d'éléments personnalisés dans Visual Studio](../ide/creating-project-and-item-templates.md)  
  
  