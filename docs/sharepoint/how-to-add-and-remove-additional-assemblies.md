---
title: 'Comment : ajouter et supprimer des assemblys supplémentaires | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 07b9016a4e246d3ed5a2697d924f556517a8226f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014830"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Comment : ajouter et supprimer des assemblys supplémentaires
  Si un package SharePoint dépend d’autres assemblys pour des fonctionnalités ou des données, vous pouvez ajouter les assemblys à votre package de solution (. wsp). De cette façon, le serveur SharePoint vérifie que les assemblys personnalisés sont installés avec un package.

 Vous pouvez également ajouter et modifier les contrôles sécurisés et les fichiers de ressources de classe associés aux assemblys.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Ajouter des assemblys, des contrôles sécurisés et des ressources de classe supplémentaires
 Vous pouvez ajouter des assemblys supplémentaires dans le package de solution SharePoint. Les assemblys supplémentaires d’une solution bac à sable (sandbox) sont déployés sur le Global Assembly Cache, mais les éléments de projet SharePoint dans une solution bac à sable (sandbox) sont ajoutés à la base de données de contenu. Vous pouvez également ajouter des contrôles sécurisés et des ressources de classe à ces assemblys supplémentaires. Pour plus d’informations sur les contrôles sécurisés, consultez [fourniture d’informations sur l’empaquetage et le déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) ou « création d’une entrée SafeControl » dans déploiement d' [composants WebPart dans SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>Pour ajouter un assembly existant

1. Ouvrez le **Concepteur de packages**. Pour plus d’informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Sélectionnez l’onglet **Avancé**.

3. Cliquez sur le bouton **Ajouter** , puis choisissez **Ajouter un assembly existant** dans la liste.

     La boîte de dialogue **Ajouter un assembly existant** s’affiche.

4. Cliquez sur les points de suspension (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")), puis sélectionnez l’assembly que vous souhaitez ajouter. Nous vous recommandons d’utiliser un chemin d’accès relatif à l’assembly sélectionné à des fins de portabilité.

5. Pour la **cible de déploiement**, sélectionnez la case d’option **GlobalAssemblyCache** pour déployer l’assembly sur le global assembly cache ou choisissez la case d’option **WebApplication** pour déployer l’assembly dans le dossier WebApplication sur le serveur qui exécute SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Pour ajouter un assembly à partir de la sortie du projet

1. Ouvrez le **Concepteur de packages**.

     Pour plus d’informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Sélectionnez l’onglet **Avancé**.

3. Cliquez sur le bouton **Ajouter** , puis choisissez **Ajouter un assembly à partir** de la sortie du projet dans la liste.

     La boîte **de dialogue Ajouter un assembly à partir de la sortie du projet** s’affiche.

4. Dans la liste **projet source** , choisissez le projet source que vous souhaitez ajouter.

5. Pour la **cible de déploiement**, sélectionnez la case d’option **GlobalAssemblyCache** pour déployer l’assembly sur le global assembly cache ou choisissez la case d’option **WebApplication** pour déployer l’assembly dans le dossier WebApplication sur le serveur qui exécute SharePoint.

#### <a name="to-add-a-safe-control"></a>Pour ajouter un contrôle sécurisé

1. Ouvrez la boîte de dialogue **modifier un assembly existant** . Pour ce faire, ouvrez le concepteur de packages, choisissez l’onglet **avancé** , choisissez un assembly, puis cliquez sur le bouton **modifier** .

2. Dans le volet **contrôles sécurisés** , choisissez le bouton **cliquez ici pour ajouter un nouvel élément** .

3. Dans la colonne nom de l' **assembly** , entrez le nom de l’assembly.

4. Dans la colonne **espace de noms** , entrez le nom de l’espace de noms pour le contrôle sécurisé.

5. Dans la colonne **nom de type** , entrez le nom du type.

#### <a name="to-add-a-class-resource"></a>Pour ajouter une ressource de classe

1. Ouvrez la boîte de dialogue **modifier un assembly existant** . Pour ce faire, ouvrez le concepteur de packages, choisissez l’onglet **avancé** , choisissez un assembly, puis cliquez sur le bouton **modifier** .

2. Dans le volet ressources de la **classe** , cliquez sur le bouton **cliquez ici pour ajouter un nouvel élément** .

3. Dans la colonne **nom de fichier** , choisissez les points de suspension (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")), puis choisissez la ressource de classe que vous souhaitez ajouter.

## <a name="delete-custom-assemblies"></a>Supprimer les assemblys personnalisés
 Vous pouvez supprimer des assemblys d’un package SharePoint, ou supprimer des contrôles sécurisés et des ressources de classe d’assemblys existants.

#### <a name="to-delete-an-existing-assembly"></a>Pour supprimer un assembly existant

1. Ouvrez le **Concepteur de packages**. Pour plus d’informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Sélectionnez l’onglet **Avancé**.

3. Dans le volet **assemblys supplémentaires** , choisissez l’assembly personnalisé que vous souhaitez supprimer.

4. Choisissez le bouton **Supprimer**.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Pour supprimer un contrôle sécurisé d’un assembly

1. Ouvrez la boîte de dialogue **modifier un assembly existant** . Pour ce faire, ouvrez le concepteur de packages, choisissez l’onglet **avancé** , choisissez un assembly, puis cliquez sur le bouton **modifier** .

2. Choisissez le contrôle sécurisé que vous souhaitez supprimer.

3. Choisissez la touche Suppr.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Pour supprimer une ressource de classe pour un assembly

1. Ouvrez la boîte de dialogue **modifier un assembly existant** . Pour ce faire, ouvrez le concepteur de packages, choisissez l’onglet **avancé** , choisissez un assembly, puis cliquez sur le bouton **modifier** .

2. Choisissez la ressource de classe que vous souhaitez supprimer.

3. Choisissez la touche Suppr.

## <a name="see-also"></a>Voir aussi
- [Créer des fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Guide pratique pour personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
