---
title: Fournir l’automatisation du code ( Microsoft Docs
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
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705993"
---
# <a name="providing-automation-for-code"></a>Fourniture de l’automatisation pour le code
La création d’un modèle d’automatisation pour votre code n’est pas nécessaire. Le SDK Environnement ne fournit pas d’échantillon pour le faire. Pour avoir un aperçu <xref:EnvDTE.CodeModel> des modèles de code, consultez l’objet.

 Pour implémenter un modèle de code, vous devez implémenter toutes les interfaces déterminées par votre structure de données interne. Les objets doivent être `IDispatch` dérivés de la classe.

 Les objets que <xref:EnvDTE.CodeModel> vous <xref:EnvDTE.FileCodeModel>étendez, <xref:EnvDTE.Project> et , sont disponibles à partir de l’objet, et ressemblent à ce qui suit:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Vous pouvez choisir d’implémenter uniquement `CodeModel` l’interface ou l’interface `FileCodeModel` de l’objet que vous revenez de votre `Project` et <xref:EnvDTE.ProjectItem> des objets. Fournissez toutes les fonctionnalités de cette interface qui convient à votre système de projet.

 Si vous souhaitez ajouter des fonctionnalités, telles que des `CodeModel` méthodes `FileCodeModel` ou des propriétés, qui ne sont pas disponibles à partir de la norme et des interfaces, créez votre propre interface qui hérite de la norme. Assurez-vous de le documenter avec votre système de projet afin que les utilisateurs finaux sachent le chercher. Vous retournez l’interface standard, `QueryInterface` mais l’utilisateur peut appeler la méthode ou le lancer sur votre interface si elle est connue pour exister.

## <a name="see-also"></a>Voir aussi
- [Modèle d’automatisation](../../extensibility/internals/automation-model-overview.md)
