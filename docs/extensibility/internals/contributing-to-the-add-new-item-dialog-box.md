---
title: "Faisant partie de la bo&#238;te de dialogue Nouvel &#233;l&#233;ment Ajouter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Boîte de dialogue Nouvel élément, qui contribuent à ajouter"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Faisant partie de la bo&#238;te de dialogue Nouvel &#233;l&#233;ment Ajouter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un sous\-type de projet peut fournir un nouveau répertoire complet des éléments pour la boîte de dialogue d' **Ajouter un nouvel élément** en enregistrant des modèles d' **Ajouter un élément** sous la sous\-clé de Registre d' `Projects` .  
  
## L'enregistrement des modèles ajouter un nouvel élément  
 Cette section se trouve sous **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** dans le Registre.  Les entrées du Registre ci\-dessous supposent qu'il existe un projet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] forme par un sous\-type hypothétique de projet.  les entrées pour le projet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont répertoriées ci\-dessous.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 La sous\-clé d' `AddItemTemplates\TemplateDirs` contient des entrées du Registre avec le chemin d'accès au répertoire dans lequel les éléments rendus disponibles dans la boîte de dialogue d' **Ajouter un nouvel élément** sont placés.  
  
 l'environnement charge automatiquement toutes les données d' `AddItemTemplates` sous la sous\-clé de Registre d' `Projects` .  Cela peut inclure des données pour les mise en ? uvre de projet de base ainsi que des données pour les types de sous\-type de projet spécifique.  chaque sous\-type de projet est identifié par un type `GUID`de projet.  Sous\-type de projet peut spécifier qu'un ensemble de mosaïques modèles d' `Add Item` doit être utilisé pour une instance de projet assaisonnée spécifique en prenant en charge l'énumération d' `VSHPROPID_ AddItemTemplatesGuid` d' <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> dans l'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> pour retourner la valeur GUID du sous\-type de projet.  si la propriété d' `VSHPROPID_AddItemTemplatesGuid` n'est pas spécifiée, le GUID du projet de base est utilisé.  
  
 vous pouvez filtrer des éléments dans la boîte de dialogue d' **Ajouter un nouvel élément** en implémentant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> sur l'objet d'agrégation de sous\-type de projet.  Par exemple, un sous\-type de projet qui implémente un projet de base de données en combinant un projet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , peut filtrer les éléments spécifiques de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de la boîte de dialogue d' **Ajouter un nouvel élément** en implémentant le filtrage, puis, peut ajouter certains éléments du projet de base de données en prenant en charge `VSHPROPID_ AddItemTemplatesGuid` dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  Pour plus d'informations sur le filtrage et ajouter des éléments à la boîte de dialogue d' **Ajouter un nouvel élément** , consultez l' [Ajout d'éléments à l'ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)