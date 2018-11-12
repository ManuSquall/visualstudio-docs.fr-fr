---
title: Comment gérer les configurations de service et des profils | Microsoft Docs
description: Découvrez comment travailler avec des fichiers de configuration de service configurations et des profils | lequel stocker les paramètres pour les environnements de déploiement et paramètres de publication des services cloud.
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001994"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Guide pratique pour gérer les configurations et les profils de service
## <a name="overview"></a>Vue d'ensemble
Lorsque vous publiez un service cloud, Visual Studio stocke les informations de configuration dans deux types de fichiers de configuration : configurations et des profils de service. Configurations de service (fichiers .cscfg) stockent les paramètres pour les environnements de déploiement pour un service cloud Azure. Azure utilise ces fichiers de configuration lorsqu’il gère vos services cloud. En revanche, magasin de profils (fichiers .azurePubxml) paramètres de publication des services cloud. Ces paramètres sont un enregistrement de ce que vous sélectionnez lorsque vous utilisez l’Assistant Publication et sont utilisés localement par Visual Studio. Cette rubrique explique comment utiliser les deux types de fichiers de configuration.

## <a name="service-configurations"></a>Configurations de service
Vous pouvez créer plusieurs configurations de service à utiliser pour chacun de vos environnements de déploiement. Par exemple, vous pouvez créer une configuration de service pour l’environnement local que vous utilisez pour exécuter et tester une application Azure et une autre configuration de service pour votre environnement de production.

Vous pouvez ajouter, supprimer, renommer et modifier ces configurations de service selon vos besoins. Vous pouvez gérer ces configurations de service à partir de Visual Studio, comme indiqué dans l’illustration suivante.

![Gérer des configurations de service](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Vous pouvez également ouvrir le **gérer les Configurations** boîte de dialogue pages de propriétés du rôle. Pour ouvrir les propriétés d’un rôle dans votre projet Windows Azure, ouvrez le menu contextuel pour ce rôle, puis choisissez **propriétés**. Sur le **paramètres** onglet, développez le **Configuration du Service** liste, puis sélectionnez **gérer** pour ouvrir le **gérer les Configurations** boîte de dialogue.

### <a name="to-add-a-service-configuration"></a>Pour ajouter une configuration de service
1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet Azure, puis sélectionnez **gérer les Configurations**.
   
    Le **gérer les Configurations de Service** boîte de dialogue s’affiche.
2. Pour ajouter une configuration de service, vous devez créer une copie d’une configuration existante. Pour ce faire, choisissez la configuration que vous souhaitez copier dans la liste nom, puis sélectionnez **créer une copie**.
3. (Facultatif) Pour donner un nom différent à la configuration du service, sélectionnez la nouvelle configuration de service dans la liste nom, puis **renommer**. Dans le **nom** texte, tapez le nom que vous souhaitez utiliser pour cette configuration de service, puis sélectionnez **OK**.
   
    Un nouveau fichier de configuration de service nommé ServiceConfiguration. [Nouveau nom] .cscfg est ajouté au projet Azure dans l’Explorateur de solutions.

### <a name="to-delete-a-service-configuration"></a>Pour supprimer une configuration de service
1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet Azure, puis sélectionnez **gérer les Configurations**.
   
    Le **gérer les Configurations de Service** boîte de dialogue s’affiche.
2. Pour supprimer une configuration de service, choisissez la configuration que vous souhaitez supprimer de la **nom** liste, puis sélectionnez **supprimer**. Une boîte de dialogue s’affiche pour vérifier que vous souhaitez supprimer cette configuration.
3. Sélectionnez **supprimer**.
   
     Le fichier de configuration de service est supprimé du projet Azure dans l’Explorateur de solutions.

### <a name="to-rename-a-service-configuration"></a>Pour renommer une configuration de service
1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet Azure, puis sélectionnez **gérer les Configurations**.
   
    Le **gérer les Configurations de Service** boîte de dialogue s’affiche.
2. Pour renommer une configuration de service, sélectionnez la nouvelle configuration de service à partir de la **nom** liste, puis sélectionnez **renommer**. Dans le **nom** texte, tapez le nom que vous souhaitez utiliser pour cette configuration de service, puis sélectionnez **OK**.
   
    Le nom du fichier de configuration du service est modifié dans le projet Azure dans l’Explorateur de solutions.

### <a name="to-change-a-service-configuration"></a>Pour modifier une configuration de service
* Si vous souhaitez modifier une configuration de service, ouvrez le menu contextuel pour le rôle spécifique que vous souhaitez modifier dans le projet Azure, puis sélectionnez **propriétés**. Consultez [Comment : configurer les rôles pour un Service de Cloud Azure avec Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) pour plus d’informations.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Rendre les différentes combinaisons de paramètres à l’aide de profils
En utilisant un profil, vous pouvez renseigner automatiquement le **Assistant Publication** avec différentes combinaisons de paramètres à des fins différentes. Par exemple, vous pouvez créer un profil pour le débogage et un autre pour la mise en production génère. Dans ce cas, votre **déboguer** profil aurait **IntelliTrace** activée et le **déboguer** configuration sélectionnée et votre **version** profil aurait **IntelliTrace** désactivé et le **version** configuration sélectionnée. Vous pouvez également utiliser des profils différents pour déployer un service à l’aide d’un autre compte de stockage.

Lorsque vous exécutez l’Assistant pour la première fois, un profil par défaut est créé. Visual Studio stocke le profil dans un fichier comportant l’extension .azurePubXml, qui est ajoutée à votre projet Azure sous la **profils** dossier. Si vous spécifiez manuellement les différents choix lorsque vous exécutez l’Assistant plus tard, le fichier met automatiquement à jour. Avant d’exécuter la procédure suivante, vous devez avoir déjà publié votre service cloud au moins une fois.

### <a name="to-add-a-profile"></a>Pour ajouter un profil
1. Ouvrez le menu contextuel pour votre projet Windows Azure, puis sélectionnez **publier**.
2. À côté du **profil cible** liste, sélectionnez le **enregistrer le profil** bouton, comme le montre l’illustration suivante. Cela crée un profil pour vous.
   
    ![Créer un nouveau profil](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Une fois le profil est créé, sélectionnez **< gérer... >** dans le **profil cible** liste.
   
    Le **gérer les profils** boîte de dialogue s’affiche, comme le montre l’illustration suivante.
   
    ![Boîte de dialogue profils gérer](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. Dans le **nom** liste, choisissez un profil, puis sélectionnez **créer une copie**.
5. Choisissez le **fermer** bouton.
   
    Le nouveau profil apparaît dans la liste profil cible.
6. Dans le **profil cible** liste, sélectionnez le profil que vous venez de créer. Les paramètres de l’Assistant publication sont renseignés avec les options du profil que vous avez sélectionné.
7. Sélectionnez le **précédent** et **suivant** boutons pour afficher chaque page de l’Assistant Publication, puis personnalisez les paramètres pour ce profil. Consultez [Assistant Publication d’Application Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) pour plus d’informations.
8. Une fois que vous avez terminé la personnalisation des paramètres, sélectionnez **suivant** pour revenir à la page Paramètres. Le profil est enregistré lorsque vous publiez le service à l’aide de ces paramètres ou si vous sélectionnez **enregistrer** en regard de la liste des profils.

### <a name="to-rename-or-delete-a-profile"></a>Pour renommer ou supprimer un profil
1. Ouvrez le menu contextuel pour votre projet Windows Azure, puis sélectionnez **publier**.
2. Dans le **profil cible** liste, sélectionnez **gérer**.
3. Dans le **gérer les profils** boîte de dialogue, sélectionnez le profil que vous souhaitez supprimer, puis sélectionnez **supprimer**.
4. Dans la boîte de dialogue de confirmation qui s’affiche, sélectionnez **OK**.
5. Sélectionnez **fermer**.

### <a name="to-change-a-profile"></a>Pour modifier un profil
1. Ouvrez le menu contextuel pour votre projet Windows Azure, puis sélectionnez **publier**.
2. Dans le **profil cible** liste, sélectionnez le profil que vous souhaitez modifier.
3. Sélectionnez le **précédent** et **suivant** boutons pour afficher chaque page de l’Assistant Publication, puis modifiez les paramètres souhaités. Consultez [Assistant Publication d’Application Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) pour plus d’informations.
4. Une fois que vous avez terminé la modification des paramètres, sélectionnez **suivant** pour revenir à la **paramètres** page.
5. (Facultatif) sélectionnez **publier** pour publier le service cloud avec les nouveaux paramètres. Si vous ne souhaitez pas publier votre service cloud pour l’instant, et que vous fermez l’Assistant Publication, Visual Studio vous demande si vous souhaitez enregistrer les modifications apportées au profil.

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur la configuration des autres parties de votre projet Azure à partir de Visual Studio, consultez [configuration d’un projet Azure](http://go.microsoft.com/fwlink/p/?LinkID=623075)

