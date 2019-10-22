---
title: Lier des éléments de modèle et des éléments de travail | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657632"
---
# <a name="link-model-elements-and-work-items"></a>Lier des éléments de modèle et des éléments de travail
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Suivez les tâches, les cas de test, les bogues, les spécifications, les problèmes et d’autres travaux liés à votre modèle en liant les éléments de modèle dans Visual Studio et les éléments de travail dans Team Foundation Server ou Visual Studio Team Services. Joignez des documents aux éléments de travail liés pour les associer à des éléments de modèle.

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Vous devez utiliser Team Explorer pour créer et ouvrir des liens. Vérifiez que votre projet et vos schémas de modélisation sont archivés dans la gestion de version afin que d'autres personnes puissent ouvrir des schémas liés.

 Par exemple, vous pouvez lier :

- un élément de travail Récit utilisateur et un diagramme d'activités pour montrer comment réaliser le récit sous la forme d'une séquence d'opérations ;

- un cas d'usage dans un diagramme de cas d'usage et des éléments de travail Cas de test pour garantir l'implémentation du cas d'usage ;

- un attribut dans une classe dans un diagramme de classes UML et un élément de travail Bogue pour montrer une erreur dans l'implémentation de l'attribut ;

- un composant dans un diagramme de composant et un élément de travail Tâche pour suivre le développement du composant. Ce type de tâche est généralement décomposée en tâches moins importantes

  Vous pouvez lier des éléments de travail à tous les éléments que vous pouvez sélectionner dans les diagrammes de modélisation ou dans l'Explorateur de modèles UML, par exemple :

- tous les éléments des modèles UML, tels que les classes, les lignes de vie, les cas d'usage, les sous-systèmes, les activités, les nœuds d'objet, les composants et les interfaces UML ;

- toutes les relations des modèles UML, telles que les associations, les généralisations, les dépendances, les flux et les messages ;

- les parties d'éléments, telles que les attributs et opérations de classes, les occurrences d'exécution de lignes de vie, les broches d'entrée et de sortie d'activités, et les parties et les ports de composants ;

- les couches et les dépendances de couches ;

- les commentaires et les liens de commentaires ;

- les diagrammes. Pour sélectionner un diagramme, choisissez une partie vide du diagramme.

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d’essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

- [Se connecter à un projet d’équipe](#ConnectTFS)

- [Lier un élément de modèle à un nouvel élément de travail](#LinkNew)

- [Lier un élément de modèle à un élément de travail existant](#LinkExisting)

- [Afficher les éléments de travail liés à un élément de modèle](#OpenWorkItem)

- [Afficher les éléments de modèle liés à un élément de travail](#ViewLinkedModels)

- [Supprimer les liens entre les éléments de modèle et les éléments de travail](#RemoveLinks)

- [Résolution des problèmes](#Troubleshooting)

## <a name="ConnectTFS"></a>Se connecter à un projet d’équipe
 Vous devez d'abord vous connecter à votre projet d'équipe pour créer, consulter ou supprimer des liens.

1. Dans le menu **Équipe** , choisissez **Gérer les connexions** pour afficher la fenêtre Team Explorer.

2. Si le projet approprié n'apparaît pas, dans Team Explorer, choisissez **Gérer les connexions** , puis **Se connecter au projet d'équipe**. Choisissez les projets appropriés ou le serveur si nécessaire.

3. Dans **Team Explorer**, choisissez le projet dans lequel vous souhaitez créer, lier ou consulter des éléments de travail.

## <a name="LinkNew"></a>Lier un élément de modèle à un nouvel élément de travail

1. Vérifiez que vous êtes connecté à l'instance TFS que vous souhaitez utiliser.

2. Sur le diagramme de modélisation ou dans l' **Explorateur de modèles UML**, ouvrez le menu contextuel de l'élément de modèle.

3. Choisissez **Créer un élément de travail** et le type d'élément de travail que vous souhaitez créer.

4. Renseignez les champs du formulaire d'élément de travail. Choisissez **Enregistrer l'élément de travail**.

     Visual Studio lie l'élément de modèle au nouvel élément de travail. Une icône apparaît sur l'élément de modèle ou près de celui-ci.

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d’essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

## <a name="LinkExisting"></a>Lier un élément de modèle à un élément de travail existant
 Quand vous liez des éléments de modèle à des éléments de travail, commencez par l'élément de modèle, et non pas par l'élément de travail.

1. Vérifiez que vous êtes connecté à l'instance TFS que vous souhaitez utiliser.

2. Sur le diagramme de modélisation ou dans l' **Explorateur de modèles UML**, ouvrez le menu contextuel de l'élément de modèle. Choisissez **Lier à l'élément de travail**. Sélectionnez ensuite votre projet dans le champ **Projet** .

3. Choisissez un ou plusieurs éléments de travail à lier à l'élément de modèle, à l'aide de l'une des étapes suivantes :

    - Choisissez une requête dans **Requête enregistrée**.

    - Tapez les ID d'un ou de plusieurs éléments de travail, séparés par des espaces, dans **ID**.

    - Tapez un mot ou une phrase dans **Le titre contient**.

4. Choisissez **Rechercher**.

5. Dans la liste des éléments de travail, sélectionnez l'élément de travail ou les éléments de travail que vous souhaitez lier.

     Quand vous avez terminé, la propriété **Éléments de travail** de l'élément de modèle affiche un nombre supérieur. Une icône apparaît également sur l'élément de modèle ou près de celui-ci.

> [!WARNING]
> Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d’essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.

## <a name="OpenWorkItem"></a>Afficher les éléments de travail liés à un élément de modèle

1. Dans **Team Explorer**, vérifiez que vous êtes connecté au projet d'équipe où les éléments de travail sont liés à l'élément de modèle.

2. Sur le diagramme de modélisation ou dans l' **Explorateur de modèles UML**, ouvrez le menu contextuel de l'élément de modèle. Choisissez **Afficher les éléments de travail** pour afficher la liste des éléments de travail liés.

    > [!NOTE]
    > Seuls les éléments de travail du serveur actuellement connecté s'affichent. Si aucun élément de travail n'apparaît, assurez-vous que vous êtes connecté au serveur approprié dans **Team Explorer**.

## <a name="ViewLinkedModels"></a>Afficher les éléments de modèle liés à un élément de travail
 Vous pouvez consulter les diagrammes et les éléments de modélisation liés à un élément de travail dans Visual Studio Team Services et dans Team Foundation Server 2012 ou version ultérieure Par exemple, un élément de travail peut être lié aux modèles de classe qui montrent la création de nouvelles classes à implémenter.

1. Dans **Team Explorer**, vérifiez que vous êtes connecté au projet d'équipe où les éléments de modèle sont liés à l'élément de travail.

    > [!NOTE]
    > Pour afficher les éléments de modèles liés, vous pouvez uniquement utiliser Team Explorer. Vous ne pouvez pas utiliser Team Web Access. Vérifiez que votre espace de travail est mappé au projet de modélisation qui contient les diagrammes ou les éléments de modélisation. Si vous n'avez pas d'espace de travail, vous devez en créer un. Consultez [Dépannage](#Troubleshooting) et [Créer et utiliser des espaces de travail](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).

2. Ouvrez l'élément de travail et choisissez **Liens**. Sous **Lien de modèle**, ouvrez le menu contextuel de l'élément de modèle lié. Choisissez **Ouvrir un élément lié**.

     ![Ouvrir un élément de modèle lié à partir d’un élément de travail](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="RemoveLinks"></a>Supprimer les liens entre les éléments de modèle et les éléments de travail
 Supprimez un élément de travail lié en partant de l'élément de modèle. De cette manière, vous supprimez correctement le lien réciproque vers cet élément de modèle de l'élément de travail. Dans le cas contraire, si vous démarrez avec l'élément de travail, le lien réciproque de l'élément de modèle vers l'élément de travail n'est pas supprimé.

1. Sur le diagramme de modélisation ou dans l' **Explorateur de modèles UML**, ouvrez le menu contextuel de l'élément de modèle.

2. Choisissez **Supprimer les éléments de travail**.

     \- ou -

    1. Choisissez **Propriétés**, puis **Éléments de travail** pour afficher le nombre d'éléments de travail liés.

    2. Dans la propriété **Éléments de travail** , choisissez le bouton de sélection **[…]** .

        > [!NOTE]
        > Seuls les éléments de travail sur le serveur actuel s'affichent. Si la liste est vide, mais que le nombre d'éléments de travail n'est pas nul, vérifiez que vous êtes connecté au serveur approprié dans **Team Explorer**.

3. Sous **Supprimer les liens aux éléments de travail**, désactivez les éléments sélectionnés que vous souhaitez dissocier. Cliquez sur **OK**.

## <a name="Troubleshooting"></a>Dépannage

|**Problème**|**Causes possibles**|**Résolution**|
|---------------|------------------------|--------------------|
|L'élément de modèle que vous souhaitez lier est introuvable.|L'élément peut être sur un diagramme dans un projet de modélisation qui se trouve dans [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Vous n'avez peut-être pas d'espace de travail mappé au diagramme.|Mappez votre espace de travail au projet de modélisation et au diagramme. Si vous n'avez pas d'espace de travail, alors vous devez en créer un.<br /><br /> Le message d'erreur qui s'affiche pour ce problème contient le chemin d'accès que vous pouvez utiliser afin de mapper votre espace de travail.<br /><br /> Consultez [Créer et utiliser des espaces de travail](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|
|L'élément de modèle lié est introuvable.|L'élément lié est peut-être sur un diagramme qui a été déplacé, renommé ou supprimé.|1. dans l’élément de travail, supprimez le lien vers l’élément de modèle.<br />2. Créez un lien à partir de l’élément de travail vers l’élément de modèle.|
|L'élément de travail ne contient pas les éléments de modèle liés que vous attendez.|Un élément de travail indique un élément de couche lié uniquement si le lien a été créé depuis l'élément de travail. Si votre équipe n'utilise pas [!INCLUDE[esprscc](../includes/esprscc-md.md)], le chemin d'accès local des diagrammes sera utilisé pour créer les liens. Si le projet de modélisation et ses diagrammes se trouvent dans [!INCLUDE[esprscc](../includes/esprscc-md.md)], tous les membres de l'équipe qui peuvent accéder au projet sont en mesure de consulter les éléments liés dans les éléments de travail.|Essayez d'actualiser l'élément de travail.|
|La suppression d'un lien vers un élément de modèle d'un élément de travail ne supprime pas le lien de l'élément de modèle vers l'élément de travail.||Supprimez le lien vers l'élément de modèle à partir de l'élément du modèle.|

## <a name="see-also"></a>Voir aussi
 [Modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md) [créer des modèles pour votre application](../modeling/create-models-for-your-app.md)
