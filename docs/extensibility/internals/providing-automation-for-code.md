---
title: Grâce à l’automatisation pour le Code | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="providing-automation-for-code"></a>Grâce à l’automatisation pour le Code
Création d’un modèle automation pour votre code n’est pas nécessaire. Le SDK de l’environnement ne fournit pas d’un échantillon pour ce faire. Pour consulter les modèles de code, consultez la <xref:EnvDTE.CodeModel> objet.  
  
 Pour implémenter un modèle de code, vous devez implémenter des interfaces qui sont déterminées par votre structure de données interne. Les objets doivent être dérivés de la `IDispatch` classe.  
  
 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel>, sont disponibles à partir de la <xref:EnvDTE.Project> de l’objet et l’aspect suivant :  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Vous pouvez choisir de mettre en œuvre uniquement le `CodeModel` ou `FileCodeModel` interface dans l’objet que vous retournez à partir de votre `Project` et <xref:EnvDTE.ProjectItem> objets. Fournir toutes les fonctionnalités à partir de cette interface est appropriée pour votre système de projet.  
  
 Si vous souhaitez ajouter des fonctionnalités, telles que les méthodes ou propriétés, qui ne sont pas disponibles à partir de la norme `CodeModel` et `FileCodeModel` interfaces, créez votre propre interface qui hérite de la norme. Veillez à documenter avec votre système de projet afin que les utilisateurs finaux seront sachent à rechercher. Retour de l’interface standard, mais l’utilisateur peut appeler le `QueryInterface` méthode ou cast à votre interface s’il existe.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)