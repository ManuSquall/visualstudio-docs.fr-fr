---
title: Automatisation du code | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203241"
---
# <a name="providing-automation-for-code"></a>Fourniture de l’automatisation pour le code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La création d’un modèle Automation pour votre code n’est pas obligatoire. Le kit de développement logiciel (SDK) Environment ne fournit pas d’exemple pour ce faire. Pour obtenir des informations sur les modèles de code, consultez l' <xref:EnvDTE.CodeModel> objet.  
  
 Pour implémenter un modèle de code, vous devez implémenter toutes les interfaces qui sont déterminées par votre structure de données interne. Les objets doivent être dérivés de la `IDispatch` classe.  
  
 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel> , sont disponibles à partir de l' <xref:EnvDTE.Project> objet et se présentent comme suit :  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Vous pouvez choisir d’implémenter uniquement l' `CodeModel` `FileCodeModel` interface ou dans l’objet que vous retournez à partir de vos `Project` objets et <xref:EnvDTE.ProjectItem> . Fournissez toutes les fonctionnalités de cette interface qui sont appropriées pour votre système de projet.  
  
 Si vous souhaitez ajouter des fonctionnalités, telles que des méthodes ou des propriétés, qui ne sont pas disponibles à partir des `CodeModel` interfaces et standard `FileCodeModel` , créez votre propre interface qui hérite de la norme. Veillez à le documenter avec votre système de projet afin que les utilisateurs finaux sachent le Rechercher. Vous retournez l’interface standard, mais l’utilisateur peut appeler la `QueryInterface` méthode ou effectuer un cast sur votre interface si elle est connue pour exister.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)
