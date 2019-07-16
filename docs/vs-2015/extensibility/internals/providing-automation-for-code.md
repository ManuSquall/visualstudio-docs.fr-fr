---
title: Fourniture de l’automatisation pour le Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203241"
---
# <a name="providing-automation-for-code"></a>Fourniture de l’automatisation pour le code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Création d’un modèle automation pour votre code n’est pas nécessaire. Le SDK de l’environnement ne fournit pas un exemple pour y parvenir. Pour des informations sur les modèles de code, consultez le <xref:EnvDTE.CodeModel> objet.  
  
 Pour implémenter un modèle de code, vous devez implémenter des interfaces qui sont déterminés par votre structure de données interne. Les objets doivent être dérivés de la `IDispatch` classe.  
  
 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel>, sont disponibles à partir de la <xref:EnvDTE.Project> de l’objet et se présenter comme suit :  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Vous pouvez choisir d’implémenter uniquement le `CodeModel` ou `FileCodeModel` interface dans l’objet que vous retournez à partir de votre `Project` et <xref:EnvDTE.ProjectItem> objets. Fournir toutes les fonctionnalités à partir de cette interface qui convient à votre système de projet.  
  
 Si vous souhaitez ajouter des fonctionnalités, telles que les méthodes ou propriétés, qui ne sont pas disponibles à partir de la norme `CodeModel` et `FileCodeModel` interfaces, créer votre propre interface qui hérite de la norme. Veillez à documenter avec votre système de projet par conséquent, les utilisateurs finaux saurez chercher. Retour de l’interface standard, mais l’utilisateur peut appeler le `QueryInterface` méthode ou cast à votre interface s’il est connu d’exister.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)
