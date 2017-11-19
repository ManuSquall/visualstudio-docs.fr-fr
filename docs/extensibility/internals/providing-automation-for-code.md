---
title: "Grâce à l’automatisation pour le Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa1c2fa5d0da738057e59cdac007c499a834bc0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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