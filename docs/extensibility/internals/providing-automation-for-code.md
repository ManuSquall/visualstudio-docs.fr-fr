---
title: "Gr&#226;ce &#224; l&#39;automatisation pour le Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Objet CodeModel"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Gr&#226;ce &#224; l&#39;automatisation pour le Code
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Création d'un modèle Automation pour votre code n'est pas obligatoire.  L'environnement Kit de développement logiciel ne fournit pas un exemple pour ce faire.  Pour l'aperçu des modèles de code, consultez l'objet d' <xref:EnvDTE.CodeModel> .  
  
 pour implémenter un modèle de code, vous devez implémenter toutes les interfaces qui sont déterminées par votre structure de données interne.  les objets doivent être dérivés de la classe d' `IDispatch`.  
  
 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel>, sont disponibles à partir de l'objet d' <xref:EnvDTE.Project> , et se présentent comme suit :  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Vous pouvez choisir d'implémenter uniquement `CodeModel` ou d'une interface `FileCodeModel` dans l'objet que vous obtenez de vos objets d' `Project` et d' <xref:EnvDTE.ProjectItem> .  Fournissez toutes les fonctionnalités de cette interface appropriée pour votre système de projet.  
  
 Si vous souhaitez ajouter des fonctionnalités, telles que les méthodes ou les propriétés, qui sont pas disponibles d' `CodeModel` les interfaces et standard d' `FileCodeModel` , créez votre propre interface qui hérite du standard.  Assurez \-vous de le documenter avec votre système de projet afin que les utilisateurs finaux sauront à rechercher.  Vous retournez l'interface standard, mais l'utilisateur peut appeler la méthode d' `QueryInterface` ou caster à l'interface si elle est réputée pour exister.  
  
## Voir aussi  
 [Vue d’ensemble du modèle Automation](../../extensibility/internals/automation-model-overview.md)