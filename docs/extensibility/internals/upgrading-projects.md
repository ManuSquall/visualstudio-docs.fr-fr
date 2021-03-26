---
title: Mise à niveau des projets | Microsoft Docs
description: Découvrez les interfaces fournies par le kit de développement logiciel (SDK) Visual Studio pour implémenter la prise en charge de la mise à niveau dans vos projets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1da17c4bca485bd32aa6604b350b8af80277670
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073350"
---
# <a name="upgrading-projects"></a>Mise à niveau des projets

Les modifications apportées au modèle de projet d’une version de Visual Studio à la suivante peuvent nécessiter la mise à niveau des projets et des solutions afin qu’ils puissent s’exécuter sur la version plus récente. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Fournit des interfaces qui peuvent être utilisées pour implémenter la prise en charge de la mise à niveau dans vos propres projets.

## <a name="upgrade-strategies"></a>Stratégies de mise à niveau

Pour prendre en charge une mise à niveau, l’implémentation de votre système de projet doit définir et implémenter une stratégie de mise à niveau. Pour déterminer votre stratégie, vous pouvez choisir de prendre en charge la sauvegarde côte à côte (SxS), la sauvegarde de copie, ou les deux.

- La sauvegarde SxS signifie qu’un projet copie uniquement les fichiers nécessitant une mise à niveau sur place, en ajoutant un suffixe de nom de fichier approprié, par exemple, « . old ».

- La sauvegarde de copie signifie qu’un projet copie tous les éléments de projet vers un emplacement de sauvegarde fourni par l’utilisateur. Les fichiers appropriés à l’emplacement du projet d’origine sont ensuite mis à niveau.

## <a name="how-upgrade-works"></a>Fonctionnement de la mise à niveau

Quand une solution créée dans une version antérieure de Visual Studio est ouverte dans une version plus récente, l’IDE vérifie le fichier solution pour déterminer s’il doit être mis à niveau. Si la mise à niveau est requise, l' **Assistant Mise à niveau** est automatiquement lancé pour guider l’utilisateur tout au long du processus de mise à niveau.

Quand une solution doit être mise à niveau, elle interroge chaque fabrique de projet pour sa stratégie de mise à niveau. La stratégie détermine si la fabrique de projets prend en charge la sauvegarde de copie ou la sauvegarde SxS. Les informations sont envoyées à l' **Assistant Mise à niveau**, qui collecte les informations requises pour la sauvegarde et présente les options applicables à l’utilisateur.

### <a name="multi-project-solutions"></a>Solutions à projets multiples

Si une solution contient plusieurs projets et que les stratégies de mise à niveau diffèrent, par exemple quand un projet C++ qui prend uniquement en charge la sauvegarde SxS et un projet Web qui prend uniquement en charge la sauvegarde de copie, les fabriques de projet doivent négocier la stratégie de mise à niveau.

La solution interroge chaque fabrique de projet pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Il appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> pour voir si les fichiers projet globaux doivent être mis à niveau et pour déterminer les stratégies de mise à niveau prises en charge. L' **Assistant Mise à niveau** est alors appelé.

Une fois que l’utilisateur a terminé l’Assistant, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est appelé sur chaque fabrique de projet pour effectuer la mise à niveau réelle. Pour faciliter la sauvegarde, les méthodes IVsProjectUpgradeViaFactory fournissent au <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service la journalisation des détails du processus de mise à niveau. Ce service ne peut pas être mis en cache.

Après la mise à jour de tous les fichiers globaux pertinents, chaque fabrique de projet peut choisir d’instancier un projet. L’implémentation du projet doit prendre en charge <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est ensuite appelée pour mettre à niveau tous les éléments de projet pertinents.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode ne fournit pas le service SVsUpgradeLogger. Ce service peut être obtenu en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

## <a name="best-practices"></a>Bonnes pratiques

Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service pour vérifier si vous pouvez modifier un fichier avant de le modifier et l’enregistrer avant de l’enregistrer. Cela aidera vos implémentations de sauvegarde et de mise à niveau à gérer les fichiers projet sous contrôle de code source, les fichiers avec des autorisations insuffisantes, etc.

Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pendant toutes les phases de la sauvegarde et de la mise à niveau pour fournir des informations sur la réussite ou l’échec du processus de mise à niveau.

Pour plus d’informations sur la sauvegarde et la mise à niveau des projets, consultez les commentaires pour IVsProjectUpgrade dans vsshell2. idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Mise à niveau de projets personnalisés

Si vous modifiez les informations persistantes dans le fichier projet entre des versions Visual Studio différentes de votre produit, vous devez prendre en charge la mise à niveau de votre fichier projet vers la version la plus récente. Pour prendre en charge la mise à niveau qui vous permet de participer à l' **Assistant Conversion de Visual Studio**, implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface. Cette interface fournit le seul mécanisme disponible pour mettre à niveau une copie. La mise à niveau du projet est une étape du processus d’ouverture de la solution. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> est implémentée par la fabrique de projet. Sinon, elle doit pouvoir être obtenue à partir de la fabrique de projet.

L’ancien mécanisme qui utilise l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> est toujours pris en charge, mais il est conçu pour mettre à niveau le système de projet pendant le processus d’ouverture du projet. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface est donc appelée par l’environnement Visual Studio même si l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface est appelée ou implémentée. Cette approche vous permet d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> pour implémenter uniquement la mise à niveau du projet et de la copie, et de déléguer le reste du travail à effectuer sur place (éventuellement au nouvel emplacement) par l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Pour obtenir un exemple d’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , consultez [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Scénarios possibles lors d’une mise à niveau de projet :

- Si le fichier présente un format récent non pris en charge par le projet, il doit retourner une erreur indiquant ce problème. Cela suppose que la version antérieure de votre produit comprend du code pour vérifier la version.

- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> est spécifié dans la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la mise à niveau est implémentée en tant que mise à niveau sur place avant l’ouverture du projet.

- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> est spécifié dans la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la mise à niveau est implémentée en tant que mise à niveau de la copie.

- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> est spécifié dans l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, l’utilisateur est invité par l’environnement à mettre à niveau le fichier projet en tant que mise à niveau sur place, une fois le projet ouvert. Par exemple, l’environnement invite l’utilisateur à effectuer la mise à niveau quand celui-ci ouvre une version antérieure de la solution.

- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> n’est pas spécifié dans l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, vous devez inviter l’utilisateur à mettre à niveau le fichier projet.

     Voici un exemple de message d’invite de mise à niveau :

     « Le projet '%1' a été créé avec une version antérieure de Visual Studio. Si vous l’ouvrez avec cette version de Visual Studio, vous ne pourrez peut-être plus l’ouvrir avec les versions antérieures de Visual Studio. Voulez-vous continuer et ouvrir ce projet ? »

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Pour implémenter IVsProjectUpgradeViaFactory

1. Implémentez la méthode de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, à savoir la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> dans votre implémentation de la fabrique de projet, ou définissez les implémentations pour qu’elles puissent être appelées à partir de votre implémentation de la fabrique de projet.

2. Si vous souhaitez effectuer une mise à niveau sur place à l’ouverture de la solution, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> en tant que paramètre `VSPUVF_FLAGS` dans votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Si vous souhaitez effectuer une mise à niveau sur place à l’ouverture de la solution, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> en tant que paramètre `VSPUVF_FLAGS` dans votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. Pour les étapes 2 et 3, vous pouvez implémenter les étapes de mise à niveau du fichier, avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, comme décrit dans la section « Implémentation d’`IVsProjectUpgade` » ci-dessous, ou déléguer la mise à niveau du fichier à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Utilisez les méthodes d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> pour publier les messages de mise à niveau à l’intention de l’utilisateur à l’aide de l’Assistant Migration de Visual Studio.

6. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> permet d’implémenter tout type de mise à niveau de fichier devant être effectuée dans le cadre de la mise à niveau du projet. Cette interface n’est pas appelée à partir de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Elle fournit un mécanisme de mise à niveau de fichiers qui font partie du système de projet, mais dont celui-ci n’a pas directement connaissance. Par exemple, cette situation peut se produire si les fichiers et les propriétés liés au compilateur ne sont pas gérés par la même équipe de développement que celle qui gère le reste du système de projet.

### <a name="ivsprojectupgrade-implementation"></a>Implémentation d’IVsProjectUpgrade

Si votre système de projet implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uniquement, il ne peut pas participer à l' **Assistant Conversion de Visual Studio**. Toutefois, même si vous implémentez l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, vous pouvez déléguer la mise à niveau du fichier à l’implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

#### <a name="to-implement-ivsprojectupgrade"></a>Pour implémenter IVsProjectUpgrade

1. Quand un utilisateur tente d’ouvrir un projet, la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> est appelée par l’environnement après l’ouverture du projet et avant toute autre action de l’utilisateur sur le projet. Si l’utilisateur a déjà été invité à mettre à niveau la solution, l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> est passé au paramètre `grfUpgradeFlags`. Si l’utilisateur ouvre un projet directement, par exemple à l’aide de la commande **Ajouter un projet existant** , l' <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> indicateur n’est pas passé et le projet doit inviter l’utilisateur à effectuer la mise à niveau.

2. En réponse à l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, le projet doit évaluer si le fichier projet a été mis à niveau. Si le projet n’a pas besoin de mettre à niveau le type de projet vers une nouvelle version, il peut simplement retourner l’indicateur <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Si le projet doit mettre à niveau le type de projet vers une nouvelle version, il doit déterminer si le fichier projet peut être modifié en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et en passant une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le paramètre `rgfQueryEdit`. Ensuite, le projet doit effectuer les opérations suivantes :

    - Si la valeur de retour de `VSQueryEditResult` dans le paramètre `pfEditCanceled` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, la mise à niveau peut continuer, car le fichier projet peut être modifié.

    - Si la valeur de retour de `VSQueryEditResult` dans le paramètre `pfEditCanceled` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et que la valeur `VSQueryEditResult` a le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> défini, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> doit retourner une erreur, car il s’agit d’un problème d’autorisation devant être résolu par l’utilisateur. Le projet doit alors effectuer les opérations suivantes :

         Signalez l’erreur à l’utilisateur en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> et en renvoyant le <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> code d’erreur à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

    - Si la valeur de `VSQueryEditResult` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et que la valeur de `VSQueryEditResultFlags` a le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> défini, le fichier projet doit être extrait en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>, ...).

4. Si l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> sur le fichier projet entraîne l’extraction du fichier et la récupération de la version la plus récente, le projet est déchargé et rechargé. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> est rappelée après la création d’une autre instance du projet. À ce deuxième appel, le fichier projet peut être écrit sur le disque. Il est recommandé que le projet enregistre une copie du fichier projet dans le format antérieur avec l’extension de fichier .OLD, qu’il apporte les modifications nécessaires pour la mise à niveau, puis qu’il enregistre le fichier projet dans le nouveau format. Là encore, si une étape de la mise à niveau échoue, la méthode doit indiquer une erreur en retournant <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Le projet est alors déchargé dans l’Explorateur de solutions.

     Il est important de bien comprendre le déroulement du processus exécuté dans l’environnement quand l’appel à la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (en spécifiant une valeur pour ReportOnly) retourne les indicateurs <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. L’utilisateur tente d’ouvrir le fichier projet.

6. L’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retourne `true`, l’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. L’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> pour ouvrir le fichier et initialiser l’objet projet, par exemple, Projet1.

9. L’environnement appelle votre implémentation d’ `IVsProjectUpgrade::UpgradeProject` pour déterminer si le fichier projet doit être mis à niveau.

10. Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passez une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> pour le paramètre `rgfQueryEdit`.

11. L’environnement retourne <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> pour `VSQueryEditResult` et le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> est défini dans `VSQueryEditResultFlags`.

12. Votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> appelle `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Cet appel peut entraîner l’extraction d’une nouvelle copie de votre fichier projet et la récupération de la version la plus récente, ainsi que la nécessité de recharger votre fichier projet. À ce stade, il y a deux cas de figure possibles :

- Si vous gérez votre propre rechargement du projet, l’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Quand vous recevez cet appel, rechargez la première instance de votre projet (Projet1) et continuez la mise à niveau de votre fichier projet. L’environnement sait que vous gérez votre propre rechargement du projet si vous retournez `true` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

- Si vous ne gérez pas votre propre rechargement du projet, retournez `false` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). Dans ce cas, avant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) retourne, l’environnement crée une autre nouvelle instance de votre projet, par exemple, Project2, comme suit :

    1. L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sur le premier objet projet (Projet1), ce qui fait passer cet objet à l’état inactif.

    2. L’environnement appelle votre implémentation d’ `IVsProjectFactory::CreateProject` pour créer une deuxième instance de votre projet (Projet2).

    3. L’environnement appelle votre implémentation d’ `IPersistFileFormat::Load` pour ouvrir le fichier et initialiser le deuxième objet projet (Projet2).

    4. L’environnement appelle `IVsProjectUpgrade::UpgradeProject` une deuxième fois pour déterminer si l’objet projet doit être mis à niveau. Toutefois, cet appel est effectué sur la nouvelle instance (la deuxième) du projet, Projet2. Il s’agit du projet qui est ouvert dans la solution.

        > [!NOTE]
        > Dans l’instance de votre premier projet, Projet1, qui est à l’état inactif, vous devez retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> à partir du premier appel à votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>.

    5. Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passez une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> pour le paramètre `rgfQueryEdit`.

    6. L’environnement retourne <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>. La mise à niveau peut continuer, car le fichier projet peut être modifié.

Si la mise à niveau échoue, retournez <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> à partir d’`IVsProjectUpgrade::UpgradeProject`. Si aucune mise à niveau n’est nécessaire ou si vous choisissez de ne pas faire la mise à niveau, gérez l’appel `IVsProjectUpgrade::UpgradeProject` comme une absence d’opération. Si vous retournez <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, un nœud d’espace réservé est ajouté à la solution pour votre projet.

## <a name="upgrading-project-items"></a>Mise à niveau d’éléments de projet

Si vous ajoutez ou gérez des éléments dans des systèmes de projet que vous n’implémentez pas, vous devrez peut-être participer au processus de mise à niveau du projet. Crystal Reports est un exemple d’élément qui peut être ajouté au système de projet.

En règle générale, les implémenteurs d’éléments de projet souhaitent tirer parti d’un projet déjà entièrement instancié et mis à niveau, car ils ont besoin de savoir ce que sont les références de projet et les autres propriétés du projet pour prendre une décision de mise à niveau.

### <a name="to-get-the-project-upgrade-notification"></a>Pour recevoir la notification de mise à niveau du projet

1. Définissez l' <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> indicateur (défini dans vsshell80. idl) dans l’implémentation de l’élément de projet. Cela entraîne le chargement automatique de votre VSPackage d’éléments de projet lorsque le shell Visual Studio détermine qu’un système de projet est en cours de mise à niveau.

2. Conseillez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> méthode.

3. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée une fois que l’implémentation du système de projet a terminé ses opérations de mise à niveau et que le nouveau projet mis à niveau est créé. Selon le scénario, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée après <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ou les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> méthodes.

### <a name="to-upgrade-the-project-item-files"></a>Pour mettre à niveau les fichiers d’éléments de projet

1. Vous devez soigneusement gérer le processus de sauvegarde de fichiers dans l’implémentation de l’élément de projet. Cela s’applique en particulier à une sauvegarde côte à côte, où le `fUpgradeFlag` paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode a la valeur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> , où les fichiers qui ont été sauvegardés sont placés le long des fichiers désignés comme « . old ». Les fichiers sauvegardés antérieurs à l’heure système de la mise à niveau du projet peuvent être désignés comme obsolètes. En outre, elles peuvent être remplacées, sauf si vous prenez des mesures spécifiques pour éviter cela.

2. Lorsque votre élément de projet reçoit une notification de la mise à niveau du projet, l' **Assistant Conversion de Visual Studio** s’affiche toujours. Par conséquent, vous devez utiliser les méthodes de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface pour fournir des messages de mise à niveau à l’interface utilisateur de l’Assistant.

## <a name="see-also"></a>Voir aussi

- [Projets](../../extensibility/internals/projects.md)
