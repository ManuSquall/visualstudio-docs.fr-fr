---
title: Automatisation du code | Microsoft Docs
description: En savoir plus sur l’implémentation d’un modèle de code, qui requiert l’implémentation d’interfaces qui sont déterminées par votre structure de données interne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8d0745ae971f4039ffccf3431614325236e63f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875854"
---
# <a name="providing-automation-for-code"></a>Fourniture de l’automatisation pour le code
La création d’un modèle Automation pour votre code n’est pas obligatoire. Le kit de développement logiciel (SDK) Environment ne fournit pas d’exemple pour ce faire. Pour obtenir des informations sur les modèles de code, consultez l' <xref:EnvDTE.CodeModel> objet.

 Pour implémenter un modèle de code, vous devez implémenter toutes les interfaces qui sont déterminées par votre structure de données interne. Les objets doivent être dérivés de la `IDispatch` classe.

 Les objets que vous étendez, <xref:EnvDTE.CodeModel> et <xref:EnvDTE.FileCodeModel> , sont disponibles à partir de l' <xref:EnvDTE.Project> objet et se présentent comme suit :

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Vous pouvez choisir d’implémenter uniquement l' `CodeModel` `FileCodeModel` interface ou dans l’objet que vous retournez à partir de vos `Project` objets et <xref:EnvDTE.ProjectItem> . Fournissez toutes les fonctionnalités de cette interface qui sont appropriées pour votre système de projet.

 Si vous souhaitez ajouter des fonctionnalités, telles que des méthodes ou des propriétés, qui ne sont pas disponibles à partir des `CodeModel` interfaces et standard `FileCodeModel` , créez votre propre interface qui hérite de la norme. Veillez à le documenter avec votre système de projet afin que les utilisateurs finaux sachent le Rechercher. Vous retournez l’interface standard, mais l’utilisateur peut appeler la `QueryInterface` méthode ou effectuer un cast sur votre interface si elle est connue pour exister.

## <a name="see-also"></a>Voir aussi
- [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)
