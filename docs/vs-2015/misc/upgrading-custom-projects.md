---
title: Mise à niveau des projets personnalisés (fr) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: c91013e7d5650e82fd9e5f6e39e28c4609e4fbfe
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037205"
---
# <a name="upgrading-custom-projects"></a>Mise à niveau de projets personnalisés
Si vous modifiez les informations persistantes dans le fichier projet entre des versions Visual Studio différentes de votre produit, vous devez prendre en charge la mise à niveau de votre fichier projet vers la version la plus récente. Pour prendre en charge la mise à niveau qui vous permet de participer à **l’Assistant de Conversion Studio Visuel**, implémentez l’interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Cette interface fournit le seul mécanisme disponible pour mettre à niveau une copie. La mise à niveau du projet est une étape du processus d’ouverture de la solution. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> est implémentée par la fabrique de projet. Sinon, elle doit pouvoir être obtenue à partir de la fabrique de projet.  
  
 L’ancien mécanisme qui utilise l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> est toujours pris en charge, mais il est conçu pour mettre à niveau le système de projet pendant le processus d’ouverture du projet. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> est donc appelée par l’environnement [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] même si l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> est appelée ou implémentée. Cette approche vous permet d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> pour implémenter uniquement la mise à niveau du projet et de la copie, et de déléguer le reste du travail à effectuer sur place (éventuellement au nouvel emplacement) par l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
 Pour un exemple <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>de mise en œuvre de , voir [échantillons VSSDK](../misc/vssdk-samples.md).  
  
 Scénarios possibles lors d’une mise à niveau de projet :  
  
- Si le fichier présente un format récent non pris en charge par le projet, il doit retourner une erreur indiquant ce problème. Cela suppose que la version antérieure de votre produit (par exemple, Visual Studio .NET 2003) inclut le code de vérification de la version.  
  
- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> est spécifié dans la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la mise à niveau est implémentée en tant que mise à niveau sur place avant l’ouverture du projet.  
  
- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> est spécifié dans la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la mise à niveau est implémentée en tant que mise à niveau de la copie.  
  
- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> est spécifié dans l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, l’utilisateur est invité par l’environnement à mettre à niveau le fichier projet en tant que mise à niveau sur place, une fois le projet ouvert. Par exemple, l’environnement invite l’utilisateur à effectuer la mise à niveau quand celui-ci ouvre une version antérieure de la solution.  
  
- Si l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> n’est pas spécifié dans l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, vous devez inviter l’utilisateur à mettre à niveau le fichier projet.  
  
     Voici un exemple de message d’invite de mise à niveau :  
  
     « Le projet '%1' a été créé avec une version antérieure de Visual Studio. Si vous l’ouvrez avec cette version de Visual Studio, vous ne pourrez peut-être plus l’ouvrir avec les versions antérieures de Visual Studio. Voulez-vous continuer et ouvrir ce projet ? »  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Pour implémenter IVsProjectUpgradeViaFactory  
  
1. Implémentez la méthode de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, à savoir la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> dans votre implémentation de la fabrique de projet, ou définissez les implémentations pour qu’elles puissent être appelées à partir de votre implémentation de la fabrique de projet.  
  
2. Si vous souhaitez effectuer une mise à niveau sur place à l’ouverture de la solution, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> en tant que paramètre `VSPUVF_FLAGS` dans votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.  
  
3. Si vous souhaitez effectuer une mise à niveau sur place à l’ouverture de la solution, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> en tant que paramètre `VSPUVF_FLAGS` dans votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.  
  
4. Pour les étapes 2 et 3, vous pouvez implémenter les étapes de mise à niveau du fichier, avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, comme décrit dans la section « Implémentation d’`IVsProjectUpgade` » ci-dessous, ou déléguer la mise à niveau du fichier à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5. Utilisez les méthodes d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> pour publier les messages de mise à niveau à l’intention de l’utilisateur à l’aide de l’Assistant Migration de Visual Studio.  
  
6. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> permet d’implémenter tout type de mise à niveau de fichier devant être effectuée dans le cadre de la mise à niveau du projet. Cette interface n’est pas appelée à partir de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Elle fournit un mécanisme de mise à niveau de fichiers qui font partie du système de projet, mais dont celui-ci n’a pas directement connaissance. Par exemple, cette situation peut se produire si les fichiers et les propriétés liés au compilateur ne sont pas gérés par la même équipe de développement que celle qui gère le reste du système de projet.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implémentation d’IVsProjectUpgrade  
 Si votre système <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> de projet ne met en œuvre que, il ne peut pas participer à **l’Assistant de Conversion Studio Visuel**. Toutefois, même si vous implémentez l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, vous pouvez déléguer la mise à niveau du fichier à l’implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Pour implémenter IVsProjectUpgrade  
  
1. Quand un utilisateur tente d’ouvrir un projet, la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> est appelée par l’environnement après l’ouverture du projet et avant toute autre action de l’utilisateur sur le projet. Si l’utilisateur a déjà été invité à mettre à niveau la solution, l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> est passé au paramètre `grfUpgradeFlags`. Si l’utilisateur ouvre un projet directement, par exemple en <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> utilisant la commande Add Existing **Project,** alors le drapeau n’est pas passé et le projet doit inciter l’utilisateur à mettre à niveau.  
  
2. En réponse à l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, le projet doit évaluer si le fichier projet a été mis à niveau. Si le projet n’a pas besoin de mettre à niveau le type de projet vers une nouvelle version, il peut simplement retourner l’indicateur <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
3. Si le projet doit mettre à niveau le type de projet vers une nouvelle version, il doit déterminer si le fichier projet peut être modifié en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et en passant une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le paramètre `rgfQueryEdit`. Ensuite, le projet doit effectuer les opérations suivantes :  
  
   - Si la valeur de retour de `VSQueryEditResult` dans le paramètre `pfEditCanceled` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, la mise à niveau peut continuer, car le fichier projet peut être modifié.  
  
   - Si la valeur de retour de `VSQueryEditResult` dans le paramètre `pfEditCanceled` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et que la valeur `VSQueryEditResult` a le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> défini, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> doit retourner une erreur, car il s’agit d’un problème d’autorisation devant être résolu par l’utilisateur. Le projet doit alors effectuer les opérations suivantes :  
  
        Signaler l’erreur à l’utilisateur en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, et retourner le code d’erreur <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
   - Si la valeur de `VSQueryEditResult` est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et que la valeur de `VSQueryEditResultFlags` a le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> défini, le fichier projet doit être extrait en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, ...).  
  
4. Si l’appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> sur le fichier projet entraîne l’extraction du fichier et la récupération de la version la plus récente, le projet est déchargé et rechargé. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> est rappelée après la création d’une autre instance du projet. À ce deuxième appel, le fichier projet peut être écrit sur le disque. Il est recommandé que le projet enregistre une copie du fichier projet dans le format antérieur avec l’extension de fichier .OLD, qu’il apporte les modifications nécessaires pour la mise à niveau, puis qu’il enregistre le fichier projet dans le nouveau format. Là encore, si une étape de la mise à niveau échoue, la méthode doit indiquer une erreur en retournant <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Le projet est alors déchargé dans l’Explorateur de solutions.  
  
    Il est important de bien comprendre le déroulement du processus exécuté dans l’environnement quand l’appel à la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (en spécifiant une valeur pour ReportOnly) retourne les indicateurs <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>.  
  
5. L’utilisateur tente d’ouvrir le fichier projet.  
  
6. L’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.  
  
7. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retourne `true`, l’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.  
  
8. L’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> pour ouvrir le fichier et initialiser l’objet projet, par exemple, Projet1.  
  
9. L’environnement appelle votre implémentation d’ `IVsProjectUpgrade::UpgradeProject` pour déterminer si le fichier projet doit être mis à niveau.  
  
10. Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passez une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le paramètre `rgfQueryEdit`.  
  
11. L’environnement retourne <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> pour `VSQueryEditResult` et le bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> est défini dans `VSQueryEditResultFlags`.  
  
12. Votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> appelle `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
    Cet appel peut entraîner l’extraction d’une nouvelle copie de votre fichier projet et la récupération de la version la plus récente, ainsi que la nécessité de recharger votre fichier projet. À ce stade, il y a deux cas de figure possibles :  
  
- Si vous gérez votre propre rechargement du projet, l’environnement appelle votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Quand vous recevez cet appel, rechargez la première instance de votre projet (Projet1) et continuez la mise à niveau de votre fichier projet. L’environnement sait que vous gérez votre propre rechargement du projet si vous retournez `true` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
- Si vous ne gérez pas votre propre rechargement du projet, retournez `false` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). Dans ce cas, avant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>[(QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) revient, l’environnement crée un autre nouveau, exemple de votre projet, par exemple, Project2, comme suit:  
  
  1. L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sur le premier objet projet (Projet1), ce qui fait passer cet objet à l’état inactif.  
  
  2. L’environnement appelle votre implémentation d’ `IVsProjectFactory::CreateProject` pour créer une deuxième instance de votre projet (Projet2).  
  
  3. L’environnement appelle votre implémentation d’ `IPersistFileFormat::Load` pour ouvrir le fichier et initialiser le deuxième objet projet (Projet2).  
  
  4. L’environnement appelle `IVsProjectUpgrade::UpgradeProject` une deuxième fois pour déterminer si l’objet projet doit être mis à niveau. Toutefois, cet appel est effectué sur la nouvelle instance (la deuxième) du projet, Projet2. Il s’agit du projet qui est ouvert dans la solution.  
  
      > [!NOTE]
      > Dans l’instance de votre premier projet, Projet1, qui est à l’état inactif, vous devez retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> à partir du premier appel à votre implémentation d’<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>. Consultez [Basic Project](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) pour voir une implémentation d’ `IVsProjectUpgrade::UpgradeProject`.  
  
  5. Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passez une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le paramètre `rgfQueryEdit`.  
  
  6. L’environnement retourne <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>. La mise à niveau peut continuer, car le fichier projet peut être modifié.  
  
  Si la mise à niveau échoue, retournez <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> à partir d’`IVsProjectUpgrade::UpgradeProject`. Si aucune mise à niveau n’est nécessaire ou si vous choisissez de ne pas faire la mise à niveau, gérez l’appel `IVsProjectUpgrade::UpgradeProject` comme une absence d’opération. Si vous retournez <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, un nœud d’espace réservé est ajouté à la solution pour votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant de conversion de studio visuel](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Mise à niveau des éléments du projet](../misc/upgrading-project-items.md)   
 [Projets](../extensibility/internals/projects.md)