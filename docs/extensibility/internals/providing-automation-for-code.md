---
title: Fourniture de l’automatisation pour le Code | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4adbc5385923e071e158734500e30a6a05832a1f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976217"
---
# <a name="providing-automation-for-code"></a>Fourniture de l’automatisation pour le code
Création d’un modèle automation pour votre code n’est pas nécessaire. Le SDK de l’environnement ne fournit pas un exemple pour y parvenir. Pour des informations sur les modèles de code, consultez le <xref:EnvDTE.CodeModel> objet.  
  
 Pour implémenter un modèle de code, vous devez implémenter des interfaces qui sont déterminés par votre structure de données interne. Les objets doivent être dérivés de la `IDispatch` classe.  
  
 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel>, sont disponibles à partir de la <xref:EnvDTE.Project> de l’objet et se présenter comme suit :  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Vous pouvez choisir d’implémenter uniquement le `CodeModel` ou `FileCodeModel` interface dans l’objet que vous retournez à partir de votre `Project` et <xref:EnvDTE.ProjectItem> objets. Fournir toutes les fonctionnalités à partir de cette interface qui convient à votre système de projet.  
  
 Si vous souhaitez ajouter des fonctionnalités, telles que les méthodes ou propriétés, qui ne sont pas disponibles à partir de la norme `CodeModel` et `FileCodeModel` interfaces, créer votre propre interface qui hérite de la norme. Veillez à documenter avec votre système de projet par conséquent, les utilisateurs finaux saurez chercher. Retour de l’interface standard, mais l’utilisateur peut appeler le `QueryInterface` méthode ou cast à votre interface s’il est connu d’exister.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)