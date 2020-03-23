---
title: Mise à niveau des projets (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303231"
---
# <a name="upgrading-projects"></a>Mise à niveau des projets

Les modifications apportées au modèle de projet d’une version de Visual Studio à l’autre peuvent nécessiter la mise à niveau de projets et de solutions afin qu’ils puissent s’exécuter sur la version la plus récente. Les [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces fournissent qui peuvent être utilisées pour mettre en œuvre le support de mise à niveau dans vos propres projets.

## <a name="upgrade-strategies"></a>Stratégies de mise à niveau

Pour soutenir une mise à niveau, la mise en œuvre de votre système de projet doit définir et mettre en œuvre une stratégie de mise à niveau. Pour déterminer votre stratégie, vous pouvez choisir de prendre en charge la sauvegarde côte à côte (SxS), la sauvegarde de copie, ou les deux.

- La sauvegarde SxS signifie qu’un projet copie uniquement les fichiers qui ont besoin d’être mis à niveau en place, en ajoutant un suffixe de nom de fichier approprié, par exemple, ".old".

- Copier la sauvegarde signifie qu’un projet copie tous les éléments du projet à un emplacement de sauvegarde fourni par l’utilisateur. Les fichiers pertinents à l’emplacement du projet d’origine sont ensuite mis à niveau.

## <a name="how-upgrade-works"></a>Fonctionnement de la mise à niveau

Lorsqu’une solution créée dans une version antérieure de Visual Studio est ouverte dans une version plus récente, l’IDE vérifie le fichier de solution pour déterminer s’il doit être mis à niveau. Si la mise à niveau est nécessaire, le **Assistant De mise à niveau** est automatiquement lancé pour guider l’utilisateur à travers le processus de mise à niveau.

Lorsqu’une solution doit être mise à niveau, elle interroge chaque usine de projets pour sa stratégie de mise à niveau. La stratégie détermine si l’usine du projet prend en charge la sauvegarde des copies ou la sauvegarde SxS. Les informations sont envoyées à **l’Assistant De Mise à niveau**, qui recueille les informations requises pour la sauvegarde et présente les options applicables à l’utilisateur.

### <a name="multi-project-solutions"></a>Solutions multi-projets

Si une solution contient plusieurs projets et que les stratégies de mise à niveau diffèrent, par exemple lorsqu’un projet CMD qui ne prend en charge que la sauvegarde SxS et un projet Web qui ne prennent en charge que la sauvegarde des copies, les usines du projet doivent négocier la stratégie de mise à niveau.

La solution interroge chaque <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>usine de projet pour . Il appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> ensuite pour voir si les fichiers de projets globaux ont besoin d’être mis à niveau et pour déterminer les stratégies de mise à niveau prises en charge. Le **Assistant De Mise à niveau** est alors invoqué.

Une fois que l’utilisateur a terminé l’assistant, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est appelé sur chaque usine de projet pour effectuer la mise à niveau réelle. Pour faciliter la sauvegarde, les méthodes IVsProjectUpgradeViaFactory fournissent le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pour enregistrer les détails du processus de mise à niveau. Ce service ne peut pas être mis en cache.

Après avoir mis à jour tous les fichiers globaux pertinents, chaque usine de projet peut choisir d’instantanéiser un projet. La mise en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>œuvre du projet doit être prise en charge . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est ensuite appelée pour mettre à niveau tous les éléments de projet pertinents.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode ne fournit pas le service SVsUpgradeLogger. Ce service peut être <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>obtenu en appelant .

## <a name="best-practices"></a>Bonnes pratiques

Utilisez <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> le service pour vérifier si vous pouvez modifier un fichier avant de l’éditer, et pouvez l’enregistrer avant de l’enregistrer. Cela aidera vos implémentations de sauvegarde et de mise à niveau à gérer les fichiers de projet sous contrôle source, les fichiers avec des autorisations insuffisantes, et ainsi de suite.

Utilisez <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> le service pendant toutes les phases de sauvegarde et de mise à niveau pour fournir des informations sur le succès ou l’échec du processus de mise à niveau.

Pour plus d’informations sur la sauvegarde et la mise à niveau des projets, voir les commentaires pour IVsProjectUpgrade dans vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Mise à niveau des projets personnalisés

Si vous modifiez les informations persistantes dans le fichier projet entre des versions Visual Studio différentes de votre produit, vous devez prendre en charge la mise à niveau de votre fichier projet vers la version la plus récente. Pour prendre en charge la mise à niveau qui vous permet de participer à **l’Assistant de Conversion Studio Visuel**, implémentez l’interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Cette interface fournit le seul mécanisme disponible pour mettre à niveau une copie. La mise à niveau du projet est une étape du processus d’ouverture de la solution. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> est implémentée par la fabrique de projet. Sinon, elle doit pouvoir être obtenue à partir de la fabrique de projet.

L’ancien mécanisme qui utilise l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> est toujours pris en charge, mais il est conçu pour mettre à niveau le système de projet pendant le processus d’ouverture du projet. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> est donc appelée par l’environnement Visual Studio même si l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> est appelée ou implémentée. Cette approche vous permet d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> pour implémenter uniquement la mise à niveau du projet et de la copie, et de déléguer le reste du travail à effectuer sur place (éventuellement au nouvel emplacement) par l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Pour un exemple <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>de mise en œuvre de , voir [échantillons VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Scénarios possibles lors d’une mise à niveau de projet :

- Si le fichier présente un format récent non pris en charge par le projet, il doit retourner une erreur indiquant ce problème. Cela suppose que l’ancienne version de votre produit comprend du code pour vérifier la version.

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

Si votre système <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> de projet ne met en œuvre que, il ne peut pas participer à **l’Assistant de Conversion Studio Visuel**. Toutefois, même si vous implémentez l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, vous pouvez déléguer la mise à niveau du fichier à l’implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

#### <a name="to-implement-ivsprojectupgrade"></a>Pour implémenter IVsProjectUpgrade

1. Quand un utilisateur tente d’ouvrir un projet, la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> est appelée par l’environnement après l’ouverture du projet et avant toute autre action de l’utilisateur sur le projet. Si l’utilisateur a déjà été invité à mettre à niveau la solution, l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> est passé au paramètre `grfUpgradeFlags`. Si l’utilisateur ouvre un projet directement, par exemple en <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> utilisant la commande Add Existing **Project,** alors le drapeau n’est pas passé et le projet doit inciter l’utilisateur à mettre à niveau.

2. En réponse à l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, le projet doit évaluer si le fichier projet a été mis à niveau. Si le projet n’a pas besoin de mettre à niveau le type de projet vers une nouvelle version, il peut simplement retourner l’indicateur <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Si le projet doit mettre à niveau le type de projet vers une nouvelle version, il doit déterminer si le fichier projet peut être modifié en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et en passant une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le paramètre `rgfQueryEdit`. Ensuite, le projet doit effectuer les opérations suivantes :

    - Si la valeur de retour de `VSQueryEditResult` dans le paramètre `pfEditCanceled` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, la mise à niveau peut continuer, car le fichier projet peut être modifié.

    - Si la valeur de retour de `VSQueryEditResult` dans le paramètre `pfEditCanceled` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> et que la valeur `VSQueryEditResult` a le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> défini, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> doit retourner une erreur, car il s’agit d’un problème d’autorisation devant être résolu par l’utilisateur. Le projet doit alors effectuer les opérations suivantes :

         Signaler l’erreur à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> l’utilisateur <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>appelant et retourner le code d’erreur à .

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

- Si vous ne gérez pas votre propre rechargement du projet, retournez `false` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). Dans ce cas, avant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>le retour (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits), l’environnement crée une autre nouvelle instance de votre projet, par exemple, Project2, comme suit :

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

Si vous ajoutez ou gérez des éléments à l’intérieur des systèmes de projet que vous n’implémentez pas, vous devrez peut-être participer au processus de mise à niveau du projet. Crystal Reports est un exemple d’élément qui peut être ajouté au système de projet.

En règle générale, les implémenteurs d’éléments de projet veulent tirer parti d’un projet déjà entièrement instantané et mis à niveau parce qu’ils ont besoin de savoir quelles sont les références du projet et quelles autres propriétés de projet sont là pour prendre une décision de mise à niveau.

### <a name="to-get-the-project-upgrade-notification"></a>Pour obtenir la notification de mise à niveau du projet

1. Réglez le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> drapeau (défini en vsshell80.idl) dans la mise en œuvre de votre élément de projet. Cela provoque votre élément de projet VSPackage à la charge automatique lorsque la coque Visual Studio détermine qu’un système de projet est en cours de mise à niveau.

2. Conseiller <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> via la méthode.

3. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> est lancée après la mise en œuvre du système de projet a terminé ses opérations de mise à niveau et le nouveau projet amélioré est créé. Selon le scénario, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>est <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>allumée <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> après le , le , ou les méthodes.

### <a name="to-upgrade-the-project-item-files"></a>Mettre à niveau les fichiers d’éléments du projet

1. Vous devez gérer soigneusement le processus de sauvegarde de fichiers dans la mise en œuvre de votre élément de projet. Cela s’applique en particulier pour une sauvegarde `fUpgradeFlag` côte <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> à côte, <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>où le paramètre de la méthode est défini, où les fichiers qui avaient été sauvegardés sont placés le long de fichiers latéraux qui sont désignés comme ".vieux". Les fichiers sauvegardés plus anciens que le temps du système lorsque le projet a été mis à niveau peuvent être désignés comme périmés. En outre, ils peuvent être écrasés à moins que vous prescriez des mesures spécifiques pour empêcher cela.

2. Au moment où votre élément de projet reçoit une notification de la mise à niveau du projet, le **Visual Studio Conversion Wizard** est toujours affiché. Par conséquent, vous devez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> utiliser les méthodes de l’interface pour fournir des messages de mise à niveau à l’interface utilisateur assistant.

## <a name="see-also"></a>Voir aussi

- [Projets](../../extensibility/internals/projects.md)
