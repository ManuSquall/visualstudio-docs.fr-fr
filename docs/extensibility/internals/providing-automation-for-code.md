---
title: Automatisation du code | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724963"
---
# <a name="providing-automation-for-code"></a>Fourniture de l’automatisation pour le code
La création d’un modèle Automation pour votre code n’est pas obligatoire. Le kit de développement logiciel (SDK) Environment ne fournit pas d’exemple pour ce faire. Pour obtenir des informations sur les modèles de code, consultez l’objet <xref:EnvDTE.CodeModel>.

 Pour implémenter un modèle de code, vous devez implémenter toutes les interfaces qui sont déterminées par votre structure de données interne. Les objets doivent être dérivés de la classe `IDispatch`.

 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel>, sont disponibles à partir de l’objet <xref:EnvDTE.Project> et se présentent comme suit :

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Vous pouvez choisir d’implémenter uniquement l' `CodeModel` ou l’interface `FileCodeModel` dans l’objet que vous retournez à partir de vos objets `Project` et <xref:EnvDTE.ProjectItem>. Fournissez toutes les fonctionnalités de cette interface qui sont appropriées pour votre système de projet.

 Si vous souhaitez ajouter des fonctionnalités, telles que des méthodes ou des propriétés, qui ne sont pas disponibles à partir des interfaces `CodeModel` et `FileCodeModel` standard, créez votre propre interface qui hérite de la norme. Veillez à le documenter avec votre système de projet afin que les utilisateurs finaux sachent le Rechercher. Vous retournez l’interface standard, mais l’utilisateur peut appeler la méthode `QueryInterface` ou effectuer un cast sur votre interface si elle est connue.

## <a name="see-also"></a>Voir aussi
- [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)